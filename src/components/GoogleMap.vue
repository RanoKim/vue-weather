<template>
  <div>
    <div id="map-canvas" ref="map"></div>
  </div>
</template>

<script>
  export default {
    name: 'google-map',
    data () {
      return {
        lat: 37.5665,
        lng: 126.9776
      }
    },
    mounted () {
      /* global google */ // google 이라는 global객체를 ESLint를 피해서 만들 수 있음
      var center = new google.maps.LatLng(37.5665, 126.9776)
      /* eslint-disable no-new */
      var map = new google.maps.Map(this.$refs.map, { // document.getElementById('map-canvas'), {
        center: center,
        zoom: 12
      })

      var marker = new google.maps.Marker({
        position: center,
        map: map
      })

      map.addListener('center_changed', () => {
        marker.setPosition(map.getCenter())
      })

      map.addListener('dragend', () => {
        this.lat = map.getCenter().lat()
        this.lng = map.getCenter().lng()
      })

      this.sendCoordinate()
    },
    methods: {
      sendCoordinate() {
        this.$bus.$emit('sendCoordinate', {
          lat: this.lat,
          lon: this.lng
        })
      }
    }
  }
</script>

<style scoped>
  #map-canvas {
    width: 400px;
    height: 600px;
  }
</style>
