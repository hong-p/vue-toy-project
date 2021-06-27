<template>
  <div id="app">
    <div class="input-container">
      <div>
        <InputText @changeText="getText"/>
      </div>
      <div>
        <InputSearchWords @changeSearchWord="getSearchWord"/>
      </div>

    </div>
    <div class="result-container">
      <Result
        :text="text"
        :searchWord="searchWord"
      />
    </div>
  </div>
</template>

<script>
import InputText from './components/InputText.vue'
import InputSearchWords from './components/InputSearchWords.vue'
import Result from './components/Result.vue'

export default {
  name: 'App',
  components: {
    InputText,
    InputSearchWords,
    Result
  },
  data(){
    return{
      text: '',
      searchWord: ''
    }
  },
  methods: {
    getSearchWord(searchWord){
      console.log('getSearchWord')
      this.searchWord = searchWord
    },
    getText(text){
      console.log('getText')
      this.text = text
    }
  },
  // updated() {
  //   console.log(`text: ${this.text}`)
  //   console.log(`searchWord: ${this.searchWord}`)
  // },
}
</script>

<style>
.input-container {
  display: grid;
  grid-template-columns:  50% 50%;
}
/* .result-container {

} */
textarea {
  resize: horizontal;
  width: 90%;
  height: 80px;
}
</style>
