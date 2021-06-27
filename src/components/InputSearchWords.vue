<template>
  <div>
    <textarea 
      ref="textArea" 
      v-model="searchWord"
      @input="changeSearchWord"
    />
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
    methods: {
      changeSearchWord(){
        this.$emit('changeSearchWord', this.searchWord)
      }
    },
    updated() {
      autosize(this.$refs.textArea)
    },
    
  }
</script>

<style scoped>

</style>