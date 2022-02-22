<template>
  <div class="campaign">
    <b-nav>
      <template #logo-append><nuxt-link to="/">Taxa turística</nuxt-link></template>
      <b-nav-item to="/cas">En castellano</b-nav-item>
    </b-nav>
    <Nuxt />
  </div>
</template>

<script>
  import BNav from '@compromis/blobby/components/nav/BNav.vue'
  import BNavItem from '@compromis/blobby/components/nav/BNavItem.vue'

  export default {
    name: 'DefaultLayout',

    components: {
      BNav,
      BNavItem
    }
  }
</script>
