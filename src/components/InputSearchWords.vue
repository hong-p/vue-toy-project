<template>
  <div>
    <textarea v-model="searchWord"/>
    <p>{{searchWord}}</p>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        searchWord: '',
      }
    }
  }
</script>

<style scoped>

</style>