<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h3> Autostart ON </h3>
    <p>Sirv Media Viewer autostarts after the script is loaded with the 'mounted' lifecycle hook</p>
<div class="container">
<div class="Sirv">
  <div data-src="https://demo.sirv.com/example.spin"></div>
  <div data-src="https://demo.sirv.com/image.jpg" data-type="zoom"></div>
  <div data-src="https://demo.sirv.com/video.mp4"></div>
</div>
<hr>
<h3>Autostart OFF</h3>
<p>Sirv Media Viewer will not initialize until you push this beautiful button below.</p>
<div v-if="!loading">
<button class="glow-on-hover" v-on:click="startSirv">Start</button>
</div>
<div class="Sirv off" data-options="autostart:off">
  <div data-src="https://demo.sirv.com/example.spin"></div>
  <div data-src="https://demo.sirv.com/image.jpg" data-type="zoom"></div>
  <div data-src="https://demo.sirv.com/video.mp4"></div>
</div>
<hr>
<h3>Custom buttons</h3>
<div class="Sirv buttons" data-options="arrows:false">
  <div data-src="https://demo.sirv.com/demo/apt/01.jpg" data-type="zoom"></div>
  <div data-src="https://demo.sirv.com/demo/apt/02.jpg" data-type="zoom"></div>
  <div data-src="https://demo.sirv.com/demo/apt/03.jpg" data-type="zoom"></div>
  <div data-src="https://demo.sirv.com/demo/apt/04.jpg" data-type="zoom"></div>
  <div data-src="https://demo.sirv.com/demo/apt/05.jpg" data-type="zoom"></div>
  <div data-src="https://demo.sirv.com/demo/apt/06.jpg" data-type="zoom"></div>
</div>
<div class="buttons">
<button class="button1 bouncy" v-on:click="previous">⬅ Previous</button>
<button class="button1 bouncy" v-on:click="next">Next ➡</button>
</div>
</div>
  </div>
</template>

<script>
export default {
  name: 'smv',
  props: {
    msg: String
  },
 data () {
    return {
      loading:false
    }
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
      typeof window.Sirv === 'undefined' ? this.loadScript('https://scripts.sirv.com/sirvjs/v3/sirv. js').then(() => {
        window.Sirv.start('.off') }) : window.Sirv.start('.off')
      // if (typeof window.Sirv === 'undefined') {
      //   this.loadScript('https://scripts.sirv.com/sirvjs/v3/sirv.js').then(() => {
      //     window.Sirv.start('.off')
      //   })
      // } else {
      //   window.Sirv.start('.off')
      // }
      this.loading = true
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
  font-size:1.4em;
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
.buttons {
  margin-top:10px;
}
.glow-on-hover {
    width: 220px;
    height: 50px;
    border: none;
    outline: none;
    color: #fff;
    background: #327bba;
    cursor: pointer;
    position: relative;
    z-index: 0;
    border-radius: 10px;
    font-size:1.1em;
}

.glow-on-hover:before {
    content: '';
    background: linear-gradient(45deg, #ff0000, #ff7300, #fffb00, #48ff00, #00ffd5, #002bff, #7a00ff, #ff00c8, #ff0000);
    position: absolute;
    top: -2px;
    left:-2px;
    background-size: 400%;
    z-index: -1;
    filter: blur(5px);
    width: calc(100% + 4px);
    height: calc(100% + 4px);
    animation: glowing 20s linear infinite;
    opacity: 0;
    transition: opacity .3s ease-in-out;
    border-radius: 10px;
}

.glow-on-hover:active {
    color: #000
}

.glow-on-hover:active:after {
    background: transparent;
}

.glow-on-hover:hover:before {
    opacity: 1;
}

.glow-on-hover:after {
    z-index: -1;
    content: '';
    position: absolute;
    width: 100%;
    height: 100%;
    background:  #327bba;
    left: 0;
    top: 0;
    border-radius: 10px;
}

@keyframes glowing {
    0% { background-position: 0 0; }
    50% { background-position: 400% 0; }
    100% { background-position: 0 0; }
}
hr {
  margin:50px;
}
button.button1{
  display:inline-block;
  font-size:1.2em;
  padding:0.35em 1.2em;
  border:0.1em solid #FFFFFF;
  margin:0 0.3em 0.3em 0;
  border-radius:0.12em;
  box-sizing: border-box;
  color:#757272;
  text-align:center;
  transition: all 0.2s;
  cursor:pointer;
}
button.button1:hover{
  color:#000000;
  background-color:#c7c2c2;
}
@media all and (max-width:30em){
button.button1{
  display:block;
  margin:0.4em auto;
}
}
.bouncy{
animation:bouncy 5s linear;
position:relative;
}
@keyframes bouncy {
  0%{top:0em}
  40%{top:0em}
  43%{top:-0.9em}
  46%{top:0em}
  48%{top:-0.4em}
  50%{top:0em}
  100%{top:0em;}
}
</style>
