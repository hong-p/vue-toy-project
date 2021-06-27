<template>
  <div>
    <p>{{text}} + {{searchWord}}</p>
  </div>
</template>

<script>
  export default {
    props: [
      'text', 'searchWord'
    ],
    data(){
      return {
        result : '',
      }
    }
  }
</script>

<style scoped>

</style>