<template>
  <div id="app">
    <!--<img src="./assets/logo.png">-->
    <!--Hello, Vue.js.-->
    <!--<hello></hello>-->



    <!--<button @click="fetchPosts">불러오기</button>-->
    <!--<ul>-->
      <!--<li v-for="post in posts">-->
        <!--<h1>{{ post.title }}</h1>-->
        <!--<p>{{ post.body }}</p>-->
      <!--</li>-->
    <!--</ul>-->


    <div id="information">
      <div id="current-weather">
      </div>

      <div id="forecast">
      </div>
    </div>

    <div id="map">
    </div>

  </div>
</template>

<script>
  export default {
    name: 'app'
  }
</script>

<style>
  body {
    background-color: #fafafa;
  }

  #app {
    pasition: absolute;
    top: 50%;
    left: 50%;
    width: 1000px;
    height: 600px;
    margin-top: -300px;
    margin-left: -500px;
    border-radius: 3px;
    background-color: #444;
    box-shadow: 0px 2px 2px 2px rgba(0, 0, 0, 0.3);
  }
  /* float 속성을 해제하는 방법 */
  #app:after {
    content: '';
    display: block;
    clear: both;
  }
  #app > #information {
    float: left;
    width: 600px;
  }
  #app > #information > #current-weather {
    height: 200px;
    background-color: blue;
  }
  #app > #information > #forecast {
    height: 400px;
    background-color: red;
  }
  #app > #map {
    float: right;
    width: 400px;
    height: 600px;
    background-color: green;
  }
</style>

<!--<script>-->
<!--import Hello from './components/Hello'-->

<!--export default {-->
  <!--name: 'app',-->
  <!--data () {-->
    <!--return {-->
      <!--posts: []-->
    <!--}-->
  <!--},-->
  <!--components: {-->
    <!--Hello-->
  <!--},-->
  <!--methods: {-->
    <!--fetchPosts () {-->
      <!--// 1. bind()-->
      <!--this.axios.get('https://jsonplaceholder.typicode.com/posts', {-->
        <!--params: {-->
          <!--userId: 1-->
        <!--}-->
      <!--}).then(function (response) {-->
          <!--this.posts = response.data-->
        <!--}.bind(this))-->

      <!--// 2. =>-->
<!--//      this.axios.get('https://jsonplaceholder.typicode.com/posts')-->
<!--//        .then((response) => {-->
<!--//          this.posts = response.data-->
<!--//        })-->

      <!--// 3. self-->
<!--//      let self = this-->
<!--//      this.axios.get('https://jsonplaceholder.typicode.com/posts')-->
<!--//        .then(function (response) {-->
<!--//          self.posts = response.data-->
<!--//        })-->

    <!--}-->
  <!--}-->
<!--}-->
<!--</script>-->

<!--<style lang="scss" scoped>-->
  <!--$point-color: #172133;-->

  <!--ul {-->
    <!--li {-->
      <!--h1 {-->
        <!--font-size: 20pt;-->
        <!--color: $point-color;-->
      <!--}-->

      <!--p {-->
        <!--font-size: 10pt;-->
        <!--color: blue;-->
      <!--}-->
    <!--}-->
  <!--}-->

  <!--/*ul li {*/-->
  <!--/*}*/-->
<!--</style>-->
