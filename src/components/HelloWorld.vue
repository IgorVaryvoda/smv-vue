<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <!-- Autostart -->
<!-- <div class="Sirv">
  <div data-src="https://demo.sirv.com/example.spin"></div>
  <div data-src="https://demo.sirv.com/image.jpg" data-type="zoom"></div>
  <div data-src="https://demo.sirv.com/video.mp4"></div>
</div> -->

<div class="Sirv" data-options="autostart:off">
  <div data-src="https://demo.sirv.com/example.spin"></div>
  <div data-src="https://demo.sirv.com/image.jpg" data-type="zoom"></div>
  <div data-src="https://demo.sirv.com/video.mp4"></div>
</div>

  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  head: {
  title: {
    inner: 'Sirv with SMV is dope as fuck'
  },
  script: [
      { type: 'text/javascript', src: 'https://scripts.sirv.com/sirvjs/v3/sirv.js'}
    ]
  },
  props: {
    msg: String
  },
  created() {
   this.initializeSirv()
  },
  methods: {
    initializeSirv() {
      if (window.Sirv == undefined) {
        this.checkSirvLoaded()
      }
    },
    checkSirvLoaded() {
      const interval = setInterval(() => {
        if(window.Sirv == undefined) {
          console.log('query');
          console.log(window.Sirv);
          this.checkSirvLoaded()
        } else {
          window.Sirv.start()
          clearInterval(interval)
        }
      }, 10);
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
</style>
