<template>
  <marquee-line class="lie-marquee" :duration="30">
      <span v-for="city in cities" :key="city.name" class="city">
        {{ city.name }}
        <span class="tax">{{ city.tax }}</span>
      </span>
  </marquee-line>
</template>

<script>
  import cities from '@/content/cities-marquee'

  export default {
    data () {
      return {
        cities
      }
    }
  }
</script>
