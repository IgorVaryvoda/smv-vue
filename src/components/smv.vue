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
<button v-on:click="startSirv">Start</button>
<div class="Sirv off" data-options="autostart:off">
  <div data-src="https://demo.sirv.com/example.spin"></div>
  <div data-src="https://demo.sirv.com/image.jpg" data-type="zoom"></div>
  <div data-src="https://demo.sirv.com/video.mp4"></div>
</div>
<h3>Custom buttons</h3>
<div class="Sirv buttons" data-options="arrows:false">
  <div data-src="https://demo.sirv.com/demo/apt/01.jpg" data-type="zoom"></div>
  <div data-src="https://demo.sirv.com/demo/apt/02.jpg" data-type="zoom"></div>
  <div data-src="https://demo.sirv.com/demo/apt/03.jpg" data-type="zoom"></div>
  <div data-src="https://demo.sirv.com/demo/apt/04.jpg" data-type="zoom"></div>
  <div data-src="https://demo.sirv.com/demo/apt/05.jpg" data-type="zoom"></div>
  <div data-src="https://demo.sirv.com/demo/apt/06.jpg" data-type="zoom"></div>
</div>
<button v-on:click="previous">Previous</button>
<button v-on:click="next">Next</button>
</div>
  </div>
</template>

<script>
export default {
  name: 'smv',
  props: {
    msg: String
  },
  methods: {
    loadScript(src) {
    return new Promise(resolve => {
      const script = document.createElement('script')
      script.src = src;
      script.type = 'text/javascript'
      script.async = true
      script.onload = resolve
      document.body.appendChild(script)
    })
    },
    startSirv() {
      this.loadScript('https://scripts.sirv.com/sirvjs/v3/sirv.js').then(() => {
        window.Sirv.start('.off')
      })
    },
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
