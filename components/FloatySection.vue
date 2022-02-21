<template>
  <section class="page-section">
    <div ref="scene" class="container">
      <slot />
    </div>
  </section>
</template>

<script>
  import Parallax from 'parallax-js'

  export default {
    mounted () {
    const scene = this.$refs.scene
    // eslint-disable-next-line
    const parallaxInstance = new Parallax(scene)
    }
  }
</script>
