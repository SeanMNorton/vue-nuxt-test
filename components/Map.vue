<template>
  <iframe
    width="280"
    height="280"
    frameborder="0"
    style="border:0"
    :src="mapsURL"
    allowfullscreen
  />
</template>

<script>
export default {
  name: 'Map',
  props: {
    lat: {
      type: String,
      default: '41.881832'
    },
    long: {
      type: String,
      default: '-87.623177'
    }
  },

  computed: {
    mapsURL () {
      return `https://maps.google.com/maps?q=${this.lat},${this.long}&t=&z=15&ie=UTF8&iwloc=&output=embed`
    }
  }
}
</script>
