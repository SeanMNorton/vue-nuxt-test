<template>
  <div class="container">
    <h1 v-if="loadingMap">
      Loading...
    </h1>
    <Card :is-portrait="true">
      <template #image>
        <Map :lat="lat" :long="long" />
      </template>

      <template #content>
        <button @click="setCurrentPosition">
          Get My Location
        </button>
      </template>

      <template #footer>
        Footer
      </template>
    </Card>
  </div>
</template>

<script>
export default {
  data () {
    return {
      lat: undefined,
      long: undefined,
      loadingMap: false
    }
  },
  methods: {
    async setCurrentPosition () {
      try {
        this.loadingMap = true
        await this.$CapacitorGeolocation.getCurrentPosition()
          .then((result) => {
            this.lat = result.coords.latitude.toString()
            this.long = result.coords.longitude.toString()
          })
      } catch (e) {
        alert('unable to find location, please try again later')
      } finally {
        this.loadingMap = false
      }
    }
  }

}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family:
    'Quicksand',
    'Source Sans Pro',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    Roboto,
    'Helvetica Neue',
    Arial,
    sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.links {
  padding-top: 15px;
}
</style>
