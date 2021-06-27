<template>
  <div id="app">
    <div>
      <h2>
        여러 단어를 검색할 수 있습니다.
      </h2>
    </div>
    <div class="input-container">
      <div>
        <InputText @changeText="getText"/>
      </div>
      <div>
        <InputSearchWords @changeSearchWord="getSearchWord"/>
      </div>

    </div>
    <div class="result-container">
      <SearchResult
        :text="text"
        :searchWord="searchWord"
      />
    </div>
  </div>
</template>

<script>
import InputText from './components/InputText.vue'
import InputSearchWords from './components/InputSearchWords.vue'
import SearchResult from './components/SearchResult.vue'

export default {
  name: 'App',
  components: {
    InputText,
    InputSearchWords,
    SearchResult
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
