<template>
  <div class="rail">
    <div class="wagon">
      <div class="tax-map">

      </div>
      <div class="background" aria-hidden="true">
        <div v-for="city in Object.values(cities)" :key="city.name" class="background-city">
          <img :src="city.image" :alt="city.name" />
        </div>
      </div>
    </div>
    
  </div>
</template>

<script>
  export default {
    data () {
      return {
        cities: {
          paris: {
            name: 'Paris',
            tax: '3€',
            description: 'per nit',
            image: require('../assets/images/cities/benidorm.jpg')
          }
        },
        currentCity: 'paris'
      }
    },

    mounted () {
      this.animateMap()
    },

    methods: {
      animateMap () {
        const tl = this.$gsap.timeline()

        tl
        .to('.tax-map', {
          scale: 1.8,
          transformOrigin: "50% bottom",
          duration: 3,
          scrollTrigger: {
            trigger: '.map-img',
            start: '1000px 500px',
            end: '1000px -1000px',
            scrub: true,
            markers: true
          }
        })
      }
    }
  }
</script>

<style lang="scss" scoped>
.rail {
  height: 2500px;
}

.wagon {
  position: sticky;
  top: 100px;
  height: 80vh;
  width: 100%;
  background: fuchsia;
}
</style>