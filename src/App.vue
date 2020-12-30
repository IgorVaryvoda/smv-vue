<template>
  <div id="app">
    <div class="center">
      <img alt="Vue logo" src="./assets/logo.png"> <span style="font-size:122px;padding: 0 20px;">+</span> <img src="https://sirv-cdn.sirv.com/website/img/sirv-logo.svg" width="250px"/>
    </div>
    <HelloWorld msg="Here's a demo of SMV in VueJS 2"/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
export default {
  name: 'App',
  components: {
    HelloWorld
  },
  head: {
  title: {
    inner: 'Sirv with SMV is dope as fuck'
  },
  script: [
      { type: 'text/javascript', src: 'https://scripts.sirv.com/sirvjs/v3/sirv.js'}
    ]
  },
mounted() {
  // let smv = document.createElement('script')
  // smv.setAttribute('src', 'https://scripts.sirv.com/sirvjs/v3/sirv.js')
  // document.head.appendChild(smv)
  this.loadScript('https://scripts.sirv.com/sirvjs/v3/sirv.js').then(() => {
    window.Sirv.start('.off')
  })
},
methods: {
  async loadScript(src) {
	return new Promise(resolve => {
		const script = document.createElement('script')
		script.src = src;
		script.type = 'text/javascript'
		script.async = true
		script.onload = resolve
		document.body.appendChild(script)
	})
  }
}
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.center {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 200px;
  border: 3px solid green;
}
</style>
