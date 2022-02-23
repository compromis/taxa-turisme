<template>
  <div class="rail">
    <div class="wagon">
      <div class="container">
        <div class="map-holder">
          <div class="tax-map">
            <map-svg @set-city="(city) => setCity(city)" @unset-city="unsetCity" />
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
            <div v-if="currentCard" class="card" :style="cardAbsolutePosition">
              <h3 class="card-title">{{ currentCityCard.name }}</h3>
              <p class="card-tax">{{ currentCityCard.tax }}</p>
              <p class="card-description">{{ currentCityCard.description }}</p>
            </div>
          </transition>
        </div>
      </div>
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

        tl.to('.tax-map', {
          scale: 1.8,
          transformOrigin: "10% bottom",
          duration: 3,
          scrollTrigger: {
            trigger: '.map-holder',
            start: '1000px 500px',
            end: '1000px -1000px',
            scrub: true,
            markers: true
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
      }
    }
  }
</script>

<style lang="scss" scoped>
@import "../assets/scss/variables";
@import "@compromis/blobby/scss/variables";

.rail {
  height: 250vh;
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
</style>