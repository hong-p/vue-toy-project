<template>
  <div>
    <textarea ref="textArea" v-model="searchWord"/>
    <p>{{searchWord}}</p>
  </div>
</template>

<script>
import autosize from 'autosize';

  export default {
    data() {
      return {
        searchWord: '',
      }
    },
    updated() {
      autosize(this.$refs.textArea)
    },
    
  }
</script>

<style scoped>

</style>