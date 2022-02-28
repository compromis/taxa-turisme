<template>
  <div class="rail">
    <div class="wagon">
      <div class="container">
        <div class="map-holder">
          <div class="tax-map">
            <map-svg :current-city="currentCity" @set-city="(city) => setCity(city)" @unset-city="unsetCity" />
          </div>
          <div class="background" aria-hidden="true">
            <div
              v-for="[ref, city] in Object.entries(cities)"
              :key="ref"
              :class="['background-city', { current: ref === currentCity }]"
              :style="{
                '--rotate': randomValue(currentCity, 'rotate'),
                '--offset-x': randomValue(currentCity, 'offsetX'),
                '--offset-y': randomValue(currentCity, 'offsetY')
              }"
            >
              <img :src="city.image" :alt="city.name" />
            </div>
          </div>
          <transition name="card">
            <div v-if="currentCard" class="card float-card" :style="cardAbsolutePosition">
              <h3 class="card-title">{{ currentCityCard.name }}</h3>
              <p class="card-tax">{{ currentCityCard.tax }}</p>
              <p class="card-description">{{ currentCityCard.description }}</p>
            </div>
          </transition>
        </div>
      </div>
    </div>
    <div ref="cityCards" class="city-cards" @scroll="handleScroll">
      <ul>
        <li v-for="[ref, city] in Object.entries(cities)" :key="ref" class="card">
          <h3 class="card-title">{{ city.name }}</h3>
          <p class="card-tax">{{ city.tax }}</p>
          <p class="card-description">{{ city.description }}</p>
        </li>
        <li class="spacer"></li>
      </ul>
    </div>
  </div>
</template>

<script> 
  import MapSvg from './MapSvg'
  import cities from '@/content/cities-map'

  export default {
    components: {
      MapSvg
    },

    data () {
      return {
        cities,
        currentCity: 'paris',
        currentCard: null,
        cardPos: null,
        randomValues: {}
      }
    },

    computed: {
      currentCityCard () {
        if (!this.currentCard) return null
        return this.cities[this.currentCard]
      },

      cardAbsolutePosition () {
        if (!this.cardPos) return null
        return {
          left: (this.cardPos.x + 20) + 'px',
          top: (this.cardPos.y + 20) + 'px'
        }
      }
    },

    mounted () {
      this.assignRandomValues()
      this.animateMap()
      window.addEventListener('mousemove', this.onMouseMove)
    },

    methods: {
      onMouseMove (e) {
        this.cardPos = {
          x: e.clientX,
          y: e.clientY
        }
      },

      animateMap () {
        const tl = this.$gsap.timeline()
        const vm = this

        tl.to('.tax-map', {
          scale: 1.8,
          transformOrigin: "10% bottom",
          duration: 3,
          scrollTrigger: {
            trigger: '.map-holder',
            start: 'bottom 100vh',
            end: 'bottom -150vh',
            scrub: true
          },
          onStart () {
            vm.currentCity = 'valencia'
          }
        })
      },

      assignRandomValues () {
        Object.keys(this.cities).forEach(city => {
          this.randomValues[city] = {
            rotate: this.randomRotate(),
            offsetX: this.randomOffset(),
            offsetY: this.randomOffset()
          }
        })
      },

      randomValue (city, prop) {
        if (!this.randomValues[city]) {
          const defaultValues = {
            rotate: '-2deg',
            offsetX: '3%',
            offsetY: '2%'
          }

          return defaultValues[prop]
        }

        return this.randomValues[city][prop]
      },

      randomRotate () {
        const degrees = this.randomNumber(4)
        return `${degrees}deg`
      },

      randomOffset () {
        const offset = this.randomNumber(4)
        return `${offset}%`
      },

      randomNumber (minMax) {
        return Math.ceil(Math.random() * minMax) * (Math.round(Math.random()) ? 1 : -1)
      },

      setCity (city) {
        this.currentCity = city
        this.currentCard = city
      },

      unsetCity () {
        this.currentCard = null
      },

      handleScroll () {
        const { cityCards } = this.$refs
        const cities = Object.keys(this.cities)
        const position = cityCards.scrollLeft + 50
        const width = cityCards.scrollWidth - 200
        const current = Math.floor(position / (width / cities.length))
        this.currentCity = cities[current]
      }
    }
  }
</script>

<style lang="scss" scoped>
@import "../assets/scss/variables";
@import "@compromis/blobby/scss/variables";
@import 'bootstrap/scss/functions';
@import 'bootstrap/scss/variables';
@import 'bootstrap/scss/mixins';

.rail {
  height: 200vh;
}

.map-holder {
  position: relative;
  height: 80vh;
}

.wagon {
  position: sticky;
  top: 0;
  height: 100vh;
  width: 100%;
  overflow: hidden;
  padding-top: 100px;
  margin-top: -100px;
}

.tax-map {
  position: relative;
  z-index: 5;
  top: -100px;

  svg {
    height: 100vh;
    width: 100%;
  }
}

.background {
  &-city {
    position: absolute;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    opacity: 0;
    transition: .25s ease;
    z-index: 1;

    img {
      border-radius: $postcard-radius;
      height: 75vh;
      width: 100%;
      object-fit: cover;
      transform: scale(0.98) rotate(var(--rotate, -1deg)) translate(var(--offset-X, 0), var(--offset-y, 0));
    }

    &.current {
      opacity: 1;
    }
  }
}

.city-cards {
  display: none;
}

.card {
  position: fixed;
  top: 0;
  left: 0;
  background: $white;
  color: $black;
  box-shadow: $shadow-default;
  z-index: 100;
  padding: 1.5rem;
  border-radius: 1rem;
  width: 300px;

  &-title {
    font-size: 2rem;
    font-weight: 500;
    letter-spacing: -0.03em;
  }

  &-tax {
    font-size: 4rem;
    letter-spacing: -0.03em;
    margin-top: 3rem;
    margin-bottom: 0;
    text-align: right;
    line-height: 1;
  }

  &-description {
    color: $gray-700;
    font-size: 1.5rem;
    text-align: right;
    margin: 0;
    line-height: 1;
  }
}

.card-enter-active, .card-leave-active {
  transition: opacity .25s, transform .25s;
}
.card-enter, .card-leave-to {
  opacity: 0;
  transform: translateY(20%);
}

@include media-breakpoint-down(md) {
  .rail {
    height: auto;
  }

  .wagon {
    height: auto;
    margin-top: 0;
    padding-top: 0;
    overflow: visible;
    position: static;
  }

  .tax-map {
    top: 0;

    svg {
      height: auto;
    }
  }

  .map-holder {
    height: auto;
  }

  .background-city img {
    height: 100%;
    width: 100%;
    border-radius: 1.75rem;
  }

  .city-cards {
    display: block;
    overflow-y: auto;
    padding: 2rem 0;
    scroll-snap-type: x mandatory;
    margin-top: -3.5rem;

    ul {
      list-style: none;
      display: flex;
    }

    .spacer {
      width: 200px;
      flex-shrink: 0;
    }

    .card {
      position: static;
      flex-shrink: 0;
      margin-right: 1rem;
      display: flex;
      flex-direction: column;
      height: 30vh;
      width: calc(100vw - 4rem);
      scroll-snap-align: center;

      &-title {
        font-size: 1.5rem;
      }

      &-tax {
        font-size: 2.5rem;
        margin-top: auto;
      }

      &-description {
        font-size: 1.25rem;
      }
    }
  }

  .float-card {
    display: none;
  }
}
</style>