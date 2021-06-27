<template>
  <div class="container">
    <div class="condition">
      <input type="radio" id="sensitive"  v-model="caseCheck" value="sensitive">
      <label for="sensitive">대소문자 구분  </label>  
      <input type="radio" id="insensitive" v-model="caseCheck" value="insensitive">
      <label for="insensitive">대소문자 구분 안함</label>
    </div>
    <h2>===== 검색 결과 =====</h2>
    <div class="result">
      <div class="total">
        <b> Total: <a href="javascript:return false;" @click="viewAll()">{{this.searchResults.length}}</a> </b> /
        <b> O: <a href="javascript:return false;" @click="viewOnelyO()">{{this.getCountO}}</a> </b> / 
        <b> X: <a href="javascript:return false;" @click="viewOnelyX()">{{this.getCountX}}</a> </b>
      </div>
    </div>
    <ul>
      <li v-for="result in this.viewResults" :key="result.id">
        {{result.exist}} : {{result.text}}
      </li>

    </ul>
  </div>
</template>

<script>
  export default {
    props: [
      'text', 'searchWord'
    ],
    data(){
      return {
        viewCondition: 'All',
        caseCheck: 'sensitive'
      }
    },
    computed: {
      searchResults(){
        return this.getSearchResult(this.text, this.searchWord, this.caseCheck)
      },
      viewResults() {
        let result = this.searchResults
        if(this.viewCondition === 'All') 
          return result
        return result.filter(one => {
          return one.exist === this.viewCondition
        })
      },
      getCountO(){
        return this.searchResults.filter(one=>{
          return one.exist === 'O'
        }).length
      },
      getCountX(){
        return this.searchResults.filter(one=>{
          return one.exist === 'X'
        }).length
      }
    },
    methods: {
      viewAll(){
        this.viewCondition = 'All'
      },
      viewOnelyO(){
        this.viewCondition = 'O'
      },
      viewOnelyX(){
        this.viewCondition = 'X'
      },
      getSearchResult(text, searchWord, caseCheck){
        let words =[];
        if(caseCheck=== 'insensitive'){
          text = text.toLowerCase()
          searchWord = searchWord.toLowerCase()
        }
        if(searchWord.includes(',')){
          searchWord = searchWord.replace(/\n/gi,'')
          searchWord = searchWord.replace(/\r/gi,'')
          words = searchWord.split(',')
        // , 로 구분되어있지 않고 \n 로 구분되어있는 경우
        }else if(searchWord.includes('\n')) {
          words = searchWord.split('\n')
        }
        while(words[words.length-1]=== ''){
          words.splice(words.length-1,1);
        }
        let countO = 0
        let countX = 0
        let output = []
        
        words.forEach(one => {  
          // 찾을 문자가 '이나 "으로 묶여있으면 제거
          one = one.replace(/['"]/gi,'')
          let result = []
          if(text.includes(one)){
            result = { text: one, exist: 'O'}
            countO++;
          }else{
            result = { text: one, exist: 'X'}
            countX++;
          }
          output.push(result)
        });
        // console.log(output);
        output.total = countO + countX
        output.O = countO
        output.X = countX

        return output
      }
    },
  }
</script>

<style scoped>
.container{
  margin: 20px;
}
.condition {
  margin-top: 10px;
  /* margin-left: 10px; */
}
.result {
  font-size: 1.5rem;
  margin-left: 30px;
  margin-top: 5px;
}
</style>
