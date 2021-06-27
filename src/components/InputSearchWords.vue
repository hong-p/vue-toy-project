<template>
  <div>
    <h4>
      검색할 단어들을 입력하세요.
      ex) hello, world, hi
    </h4>
    <textarea 
      ref="textArea" 
      v-model="searchWord"
      @input="changeSearchWord"
    />
    <!-- <p>{{this.searchWord}}</p> -->
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