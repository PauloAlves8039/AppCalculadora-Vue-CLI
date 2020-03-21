<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  }
}
</script>

<style scoped>
@font-face {
    font-family: FonteBody;
    src: url("../assets/fonts/Armata-Regular.ttf");
  }
  
</style>
