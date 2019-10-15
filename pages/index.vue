<template lang="pug">
  section.section
    .columns
      Card(title="Free" icon="github-circle")
        | hoge
      Card(title="Free" icon="github-circle")
        | hoge
      Card(title="Free" icon="github-circle")
        | hoge
</template>

<script>
import Card from '~/components/Card'

export default {
  name: 'HomePage',

  components: {
    Card
  }
}
</script>
