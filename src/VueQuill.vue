<template>
  <div id="vue-quill">
    <div id="editor-container">

    </div>
    <button class="vue-quill-btn" v-on:click="getContents">{{btnName}}</button>
  </div>
</template>

<script>
import Quill from 'quill'
import style from '../node_modules/quill/dist/quill.snow.css'

export default {
  mounted() {
    let toolbar = [
      [{ 'header': [1, 2, 3, false]}],
      ['bold', 'italic', 'underline', 'strike'],
      ['blockquote', 'code-block', 'image', 'link'],
      [{ 'list': 'ordered'}, { 'list': 'bullet' }],
    ]

    let config = {
      modules: { toolbar },
      theme: 'snow'
    }

    this.quill = new Quill('#editor-container', config)
  },
  methods: {
    getContents: function() {
      return this.quill.getContents()
    },

    setContents: function() {
      return this.quill.setContents.apply(this.quill, agreements)
    }
  },
  props: {
    height: Number,
    btnName: String
  }
}
</script>

<style>
#vue-quill {}
</style>