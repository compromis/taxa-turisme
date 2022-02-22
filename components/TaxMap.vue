<template>
  <div class="rail">
    <div class="wagon">
      <div class="container">
        <div class="map-holder">
          <div class="tax-map">
            <map-svg @city="(city) => currentCity = city" />
          </div>
          <div class="background" aria-hidden="true">
            <div
              v-for="[ref, city] in Object.entries(cities)"
              :key="ref"
              :class="['background-city', { current: ref === currentCity }]"
              :style="{
                '--rotate': randomRotate(),
                '--offset-x': randomOffsetX(),
                '--offset-y': randomOffsetY()
              }"
            >
              <img :src="city.image" :alt="city.name" />
            </div>
          </div>
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
        currentCity: 'paris'
      }
    },

    mounted () {
      this.animateMap()
    },

    methods: {
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

      randomRotate () {
        const degrees = this.randomNumber(4)
        return `${degrees}deg`
      },

      randomOffsetX () {
        const offset = this.randomNumber(4)
        return `${offset}%`
      },

      randomOffsetY () {
        const offset = this.randomNumber(4)
        return `${offset}%`
      },

      randomNumber (minMax) {
        return Math.ceil(Math.random() * minMax) * (Math.round(Math.random()) ? 1 : -1)
      }
    }
  }
</script>

<style lang="scss" scoped>
@import "../assets/scss/variables";

.rail {
  height: 2500px;
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
</style>