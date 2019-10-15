<template lang="pug">
  section.section
    editor-content(:editor="editor" v-model="content")
    editor-menu-bubble(:editor="editor" v-slot="{ commands, isActive, menu }")
      div(:class="{ 'is-active': menu.isActive }" :style="`left: ${menu.left}px; bottom: ${menu.bottom}px;`")
        button(:class="{ 'is-active': isActive.heading({ level: 1 }) }" @click="commands.heading({ level: 1 })")
          | H1
        button(:class="{ 'is-active': isActive.heading({ level: 2 }) }" @click="commands.heading({ level: 2 })")
          | H2
        button(:class="{ 'is-active': isActive.bold() }" @click="commands.bold")
          | Bold
</template>

<script>
import { Editor, EditorContent, EditorMenuBubble } from 'tiptap'

import {
  Blockquote,
  BulletList,
  CodeBlock,
  HardBreak,
  Heading,
  ListItem,
  OrderedList,
  TodoItem,
  TodoList,
  Bold,
  Code,
  Italic,
  Link,
  Strike,
  Underline,
  History,
} from 'tiptap-extensions'

export default {

  components: {
    EditorContent,
    EditorMenuBubble
  },

  data() {
    return {
      editor: null,
      content: ''
    }
  },

  mounted() {
    this.editor = new Editor({
      content: this.content,
    
      extensions: [
        new Blockquote(),
        new BulletList(),
        new CodeBlock(),
        new HardBreak(),
        new Heading({ levels: [1, 2, 3] }),
        new ListItem(),
        new OrderedList(),
        new TodoItem(),
        new TodoList(),
        new Link(),
        new Bold(),
        new Code(),
        new Italic(),
        new Strike(),
        new Underline(),
        new History(),
      ]

    })
  },

  beforeDestroy() {
    this.editor.destroy()
  }

}
</script>
