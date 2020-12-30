<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h3> Autostart ON </h3>
<div class="container">
<div class="Sirv">
  <div data-src="https://demo.sirv.com/example.spin"></div>
  <div data-src="https://demo.sirv.com/image.jpg" data-type="zoom"></div>
  <div data-src="https://demo.sirv.com/video.mp4"></div>
</div>
<h3>Autostart OFF</h3>
<div class="Sirv off" data-options="autostart:off">
  <div data-src="https://demo.sirv.com/example.spin"></div>
  <div data-src="https://demo.sirv.com/image.jpg" data-type="zoom"></div>
  <div data-src="https://demo.sirv.com/video.mp4"></div>
</div>
<h3>Custom buttons</h3>
<div class="Sirv buttons">
  <div data-src="https://demo.sirv.com/example.spin"></div>
  <div data-src="https://demo.sirv.com/image.jpg" data-type="zoom"></div>
  <div data-src="https://demo.sirv.com/video.mp4"></div>
</div>
<button v-on:click="previous">Previous</button>
<button v-on:click="next">Next</button>
</div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  methods: {
    previous() {
      if (window.Sirv.viewer.getInstance('.buttons').isReady()) {
        window.Sirv.viewer.getInstance('.buttons').prev()
      }
    },
    next() {
      if (window.Sirv.viewer.getInstance('.buttons').isReady()) {
        window.Sirv.viewer.getInstance('.buttons').next()
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.container {
  max-width:750px;
  margin: 0 auto;
}
</style>
