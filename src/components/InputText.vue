<template>
  <div>
    <h4>
      검색 대상 문자열을 입력하세요.
    </h4>
    <textarea 
      ref="textArea" 
      v-model="inputText"
      @input ="changText()"
    />
    <!-- <p>{{this.inputText}}</p> -->
  </div>
</template>

<script>
import autosize from 'autosize';

  export default {
     data() {
        return {
            inputText: '',
        }
    },
    updated() {
      autosize(this.$refs.textArea)
    },
    methods: {
      changText(){
        this.$emit('changeText', this.inputText)
      }
    }
  }
</script>

<style scoped>

</style>