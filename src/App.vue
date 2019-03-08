<template>
  <div id="app">
    <Timeline></Timeline>
  </div>
</template>

<script>
import Timeline from './components/Timeline'

export default {
  name: 'App',
  data() {
    return {
      // images: [
      //   {img: "/static/photo1.jpg"},
      //   {img: "/static/photo2.jpg"},
      //   {img: "/static/photo3.jpg"},
      //   {img: "/static/photo4.jpg"},
      //   {img: "/static/photo5.jpg"},
      // ],
    }
  },
  components: {
    Timeline
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
