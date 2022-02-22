<template>
  <span :id="id" ref="text" class="circled">
    <span class="text">
      <slot></slot>
    </span>
    <svg class="circle" width="126" height="72" viewBox="0 0 126 72" fill="none" xmlns="http://www.w3.org/2000/svg">
      <path class="circle-path" d="M57 9.99995C43.6866 15.3972 29.5051 20.3956 18.3333 29.7777C12.2816 34.86 4.33311 44.5324 6.22218 53.2222C8.29362 62.7508 23.1621 64.7438 30.7777 65.5555C48.2387 67.4166 66.4834 65.201 83.0555 59.4444C95.3453 55.1753 109.928 48.6984 118.444 38.3888C127.664 27.2284 107.008 20.2555 99.6666 17.4444C80.1044 9.95363 52.6056 1.07471 32 8.99995" stroke="#F0BE0B" stroke-width="10" stroke-linecap="round"/>
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
        const gsap = this.$gsap
        gsap.fromTo(
          `#${this.id} .circle-path`,
          {
            strokeDasharray: 300,
            strokeDashoffset: 300,
          },
          {
            strokeDashoffset: 0,
            duration: 1,
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
@import 'bootstrap/scss/functions';
@import 'bootstrap/scss/variables';
@import 'bootstrap/scss/mixins';
  .circled {
    position: relative;

    .text {
      position: relative;
      z-index: 2;
    }

    .circle {
      position: absolute;
      bottom: 0.05em;
      left: 0;
      right: 0;
      width: 100%;
      z-index: 1;

      &-path {
        stroke: #F0BE0B;
        stroke-width: 7;
        vector-effect: non-scaling-stroke;
      }
    }
  }

   @include media-breakpoint-down (md) {
     .circled .circle {
       bottom: -0.25em;

       &-path {
         stroke-width: 5;
       }
     }
   }
</style>
