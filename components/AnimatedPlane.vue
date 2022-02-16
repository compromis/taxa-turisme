<template>
  <div>
    <img src="~assets/images/plane.svg" alt="">
  </div>
</template>

<script>
  export default {
    mounted () {
      this.animatePlane()
    },

    methods: {
      animatePlane () {
        const tl = this.$gsap.timeline({
          onComplete () {
            this.restart();
          }
        });

        tl.from('.intro-plane img',
        {
          x: '-100vh',
          y: '100vh',
          ease: 'easeOut.Power1',
          duration: 2
        })
        .to('.intro-plane img', {
          x: '2vw',
          y: '-4vw',
          ease: 'linear',
          duration: 5
        })
        .to('.intro-plane img', {
          x: '100vw',
          y: '-80vh',
          ease: 'easeIn.Power1',
          duration: 10
        })
      }
    }
  }
</script>

<style lang="scss" scoped>

</style>