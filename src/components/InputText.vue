<template>
  <div>
    <textarea 
      ref="textArea" 
      v-model="inputText"
      @input ="changText()"
    />
    <p>{{inputText}}</p>
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