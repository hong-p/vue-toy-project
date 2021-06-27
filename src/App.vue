<template>
  <div id="app">
    <div class="input-container">
      <div>
        <InputText/>
      </div>
      <div>
        <InputSearchWords/>
      </div>

    </div>
    <div class="result-container">
      <p>result</p>
    </div>
  </div>
</template>

<script>
import InputText from './components/InputText.vue'
import InputSearchWords from './components/InputSearchWords.vue'

export default {
  name: 'App',
  components: {
    InputText,
    InputSearchWords
  }
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
