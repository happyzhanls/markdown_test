<template>
  <div id="jji">
    <textarea autofocus v-model="code"></textarea>
    <div v-html="compiledMarkdown"></div>
  </div>
</template>
<script>
import marked from 'marked'
var rendererMD = new marked.Renderer()
marked.setOptions({
  renderer: rendererMD,
  gfm: true,
  tables: true,
  breaks: false,
  pedantic: false,
  sanitize: false,
  smartLists: true,
  smartypants: false
})
export default {
  name: 'jji',
  data () {
    return {
      code: '# hello `java` '
    }
  },
  computed: {
    compiledMarkdown () {
      return marked(this.code, { sanitize: true })
    }
  }
}
</script>
