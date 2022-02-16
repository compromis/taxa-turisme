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
      },

      duration: {
        type: Number,
        default: 1
      },

      delay: {
        type: Number,
        default: 0 
      }
    },

    mounted () {
      this.animate()
    },

    methods: {
      animate () {
        this.$gsap.fromTo(
          `#${this.id}`,
          {
            opacity: 0
          },
          {
            opacity: 1,
            duration: this.duration,
            delay: this.delay,
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
    line-height: 1.1;
  }
</style>