<template>
  <div class="rail">
    <div class="map-img">Map</div>
  </div>
</template>

<script>
  export default {
    mounted () {
      this.animateMap()
    },

    methods: {
      animateMap () {
        const tl = this.$gsap.timeline()

        tl
        .to('.map-img', {
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

.map-img {
  position: sticky;
  top: 100px;
  height: 80vh;
  width: 100%;
  background: fuchsia;
}
</style>