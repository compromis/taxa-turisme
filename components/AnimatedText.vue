<template>
  <div :id="id" class="animated-text">
    <slot></slot>
  </div>
</template>

<script>
  export default {
    props: {
      id: {
        type: String,
        required: true
      }
    },

    mounted () {
      this.animate()
    },

    methods: {
      animate () {
        const gsap = this.$gsap
        gsap.from(
          `#${this.id}`,
          {
            opacity: 0,
            duration: 2,
            scrollTrigger: {
              trigger: `#${this.id}`,
              start: 'top center',
              toggleClass: 'active'
            }
          }
        )
      }
    }
  }
</script>

<style lang="scss" scoped>
  .animated-text {
    font-size: 40px;
  }
</style>