<template>
  <div id="app">
    <div class="center">
      <img alt="Vue logo" src="./assets/logo.png"> <span style="font-size:122px;padding: 0 20px;">+</span> <img src="https://sirv-cdn.sirv.com/website/img/sirv-logo.svg" width="250px"/>
    </div>
    <smv msg="Sirv Media Viewer with VueJS 2"/>
  </div>
</template>

<script>
import smv from './components/smv.vue'
export default {
  name: 'App',
  components: {
    smv
  },
  head: {
  title: {
    inner: 'Vue plays nice with Sirv Media Viewer'
  }
  // script: [
  //     { type: 'text/javascript', src: 'https://scripts.sirv.com/sirvjs/v3/sirv.js'}
  //   ]
  },
mounted() {
  if (typeof window.Sirv === 'undefined') {
    let smv = document.createElement('script')
    smv.setAttribute('src', 'https://scripts.sirv.com/sirvjs/v3/sirv.js')
    smv.async = true
    document.head.appendChild(smv)
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
