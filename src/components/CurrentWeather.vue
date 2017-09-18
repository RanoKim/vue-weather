<template>
  <div>
    <div class="location">{{ location }}</div>
    <div class="weather">{{ weather }}</div>
    <div class="temp">{{ temp }}C</div>
  </div>
</template>

<script scoped>
  export default {
    name: 'current-weather',
    data () {
      return {
        location: '',
        weather: '',
        temp: '',
        lat: 37.5665,
        lon: 126.9777
      }
    },
    mounted () {
//      this.$bus.$on('sendCoordinate', (payload) => {
//        console.log(payload)
//      })

      this.$bus.$on('sendCoordinate', this.receiveCoordinate)
    },
    methods: {
      setCoordinate (coord) {
        this.lat = coord.lat
        this.lon = coord.lon

        this.axios.get('https://api.openweathermap.org/data/2.5/weather', {
          params: {
            lat: this.lat,
            lon: this.lon,
            APPID: '6d718c77af6b64bb85c90503dd405800'
          }
        })
          .then(response => {
            let data = response.data
            console.log(data)
            this.location = data.name
            this.weather = data.weather[0].main
            this.temp = (data.main.temp - 273.15).toFixed(0) // toFixed(0) : 소수점없이 반올림
          })
      },
      receiveCoordinate (payload) {
        this.setCoordinate(payload)
      }
    }
  }
</script>

<style scoped>
  .location {
    text-align: center;
    font-size: 40pt;
    color: wheat;
  }
  .weather {
    text-align: center;
    font-size: 20pt;
    color: wheat;
  }
  .temp {
    text-align: center;
    font-size: 50pt;
    color: wheat;
  }
</style>
