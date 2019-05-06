<template>
  <div id="app">
    <div id="toolbar">
      <!-- <button class="ql-bold"></button>
      <button class="ql-italic">Italic</button>
      <button class="ql-image"></button> -->
      <button class="test-btn" @click="insertEmbedBlot">自定义图片插入</button>
      <!-- <button class="test-btn" @click="insertEmbedBlot">测试 embed-blot</button> -->
    </div>

    <div id="editor"> 
      <p>Hello World!</p>
    </div>
  </div>
</template>

<script>
import Quill from './quill/quill.js'
// import Quill from 'quill'
import Snow from 'quill/dist/quill.snow.css'
import ImageBlot from './blots_custom/imageBlot'
Quill.register(ImageBlot)

export default {
  name: 'app',
  data () {
    return {
      quill: null
    }
  },
  methods: {
    insertEmbedBlot () {
      let range = this.quill.getSelection(true);
      this.quill.insertText(range.index, '\n', Quill.sources.USER);
      this.quill.insertEmbed(range.index + 1, 'image1', {
        alt: 'Quill Cloud',
        url: 'https://quilljs.com/0.20/assets/images/cloud.png'
      }, Quill.sources.USER);
      this.quill.setSelection(range.index + 2, Quill.sources.SILENT);
    }
  },
  mounted () {
    this.quill = new Quill('#editor', {
      modules: { toolbar: '#toolbar' },
      theme: 'snow'
    })
    console.log('this is mounted')
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
.test-btn {
  width: 200px !important;
}
</style>
