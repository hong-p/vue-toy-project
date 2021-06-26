<template>
  <div>
    <textarea v-model="inputText"/>
    <p>{{inputText}}</p>
  </div>
</template>

<script>
  export default {
     data() {
        return {
            inputText: '',
        }
    },
    methods: {

    }
  }
</script>

<style>
textarea {
  resize: none;
}
</style>