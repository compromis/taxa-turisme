<template>
  <marquee-line class="lie-marquee" :duration="30">
      <span v-for="city in cities" :key="city.name.val" class="city">
        <span>{{ city.name[lang] }}</span>
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
    },

    computed: {
      lang() {
        return this.$route.name === 'cas' ? 'cas' : 'val'
      }
    },
  }
</script>
