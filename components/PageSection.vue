<template>
  <section class="page-section">
    <div :class="['main-container', { container: !noContainer }]">
      <slot />
    </div>
  </section>
</template>

<script>
export default {
  props: {
    noContainer: {
      type: Boolean,
      default: false
    }
  }
}
</script>
