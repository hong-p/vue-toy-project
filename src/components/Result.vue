<template>
  <div>
    <div class="result">
      Total: {{results.total}}<br>
      O: {{results.O}}<br>
      X: {{results.X}}<br>
    </div>
    <ul>
      <li v-for="result in results" :key="result.text">
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
        // result : '',
      }
    },
    computed: {
      results(){
        return this.getSearchResult(this.text, this.searchWord)
      }
    },
    methods: {
      getSearchResult(text, searchWord){
        let words =[];
        if(searchWord.includes(',')){
          searchWord = searchWord.replace(/\n/gi,'')
          searchWord = searchWord.replace(/\r/gi,'')
          words = searchWord.split(',')
        // , 로 구분되어있지 않고 \n\r 로 구분되어있는 경우
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
        console.log(output);

        console.log(`O: ${countO}`)
        console.log(`X: ${countX}`)
        output.total = countO + countX
        output.O = countO
        output.X = countX

        return output
      }
    },
  }
</script>

<style scoped>
.result {
  font-size: 1.5rem;
  margin-left: 30px;
  margin-top: 30px;
}
</style>