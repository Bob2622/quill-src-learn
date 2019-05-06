<template>
  <div id="app">
    <div id="toolbar">
      <button class="ql-bold">Bold</button>
      <button class="ql-italic">Italic</button>
    </div>

    <div id="editor">
      <p>Hello World!</p>
    </div>
  </div>
</template>

<script>
import Quill from 'quill'
import Snow from 'quill/dist/quill.snow.css'
export default {
  name: 'app',
  mounted () {
    var editor = new Quill('#editor', {
      modules: { toolbar: '#toolbar' },
      theme: 'snow'
    });
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
.quill {
  width: 100%;
  height: 600px;
  background: yellow;
}
</style>
