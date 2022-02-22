<template>
  <li :id="id" class="funding-item">
    <span class="funding-item-text">
      <slot />
    </span>
    <span class="funding-item-money">
      +€€€€
    </span>
    <div class="funding-item-image">
      <slot name="image" />
    </div>
  </li>
</template>

<script>
  export default {
    props: {
      id: {
        type: String,
        required: true
      },
    },

    mounted () {
      this.animate()
    },

    methods: {
      animate () {
        this.$gsap.to(`#${this.id}`, {
          scrollTrigger: {
            trigger: `#${this.id}`,
            start: 'center 70%',
            toggleClass: 'active'
          },
          onComplete () {
            const audio = new Audio('/sounds/cash.mp3')
            audio.play()
          }
        })
      }
    }
  }
</script>
