<template>
  <div id="app">
    <div>
      <h2>
        긴 문자열에서 여러 단어 존재하는지 확인하기!!
      </h2>
    </div>
    <div class="input-container">
      <div>
        <InputText @changeText="getText"/>
      </div>
      <div>
        <InputSearchWords @changeSearchWord="getSearchWord"/>
        <div class="result-container">
          <SearchResult
            :text="text"
            :searchWord="searchWord"
          />
        </div>
      </div>

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
#app{
  margin: 30px;
}
.input-container {
  display: grid;
  grid-template-columns:  50% 50%;
}
textarea {
  resize: horizontal;
  width: 90%;
  height: 80px;
}
</style>
