<template>
  <span :id="id" ref="text" class="underlined">
    <span class="text">
      <slot></slot>
    </span>
    <svg class="line" width="190" height="13" viewBox="0 0 190 13" fill="none" xmlns="http://www.w3.org/2000/svg" preserveAspectRatio="none">
      <path class="line-path" d="M5 7.10461C64.784 2.36924 125.079 7.10461 185 7.10461" stroke-linecap="round" />
    </svg>
  </span>
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
        const { width } = this.$refs.text.getBoundingClientRect()
        const gsap = this.$gsap
        gsap.fromTo(
          `#${this.id} .line-path`,
          {
            strokeDasharray: width,
            strokeDashoffset: width,
          },
          {
            strokeDashoffset: 0,
            duration: width / 300,
            delay: 0.75 + this.delay,
            ease: 'Linear.easeOut',
            scrollTrigger: {
              trigger: `#${this.id}`,
              start: 'center 90%',
              toggleClass: 'active'
            }
          }
        )
      }
    }
  }
</script>

<style lang="scss" scoped>
  .underlined {
    position: relative;
    white-space: nowrap;

    .text {
      position: relative;
      z-index: 2;
    }

    .line {
      position: absolute;
      bottom: 0.2em;
      left: 0;
      right: 0;
      width: 100%;
      height: 10px;
      z-index: 1;

      &-path {
        stroke: #F0BE0B;
        stroke-width: 7;
        vector-effect: non-scaling-stroke;
      }
    }
  }
</style>