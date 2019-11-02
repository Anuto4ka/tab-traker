<template>
  <panel title="Lyrics">
    <textarea
      readonly
      v-model="song.lyrics"
    ></textarea>
  </panel>
</template>

<script>

export default {
  props: [
    'song'
  ]
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  textarea{
    border:none;
    width:100%;
    height:400px;
    margin: 0em;
    font: 400 13.3333px Arial;
    font-family: monospace;
  }
</style>
