<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <!-- Autostart -->
<div class="Sirv">
  <div data-src="https://demo.sirv.com/example.spin"></div>
  <div data-src="https://demo.sirv.com/image.jpg" data-type="zoom"></div>
  <div data-src="https://demo.sirv.com/video.mp4"></div>
</div>
<!-- Autostart OFF
<div class="Sirv" data-options="autostart:off">
  <div data-src="https://demo.sirv.com/example.spin"></div>
  <div data-src="https://demo.sirv.com/image.jpg" data-type="zoom"></div>
  <div data-src="https://demo.sirv.com/video.mp4"></div>
</div>
-->
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
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
