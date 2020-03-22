<template>
  <div class="calculadora">
    <h1>{{ msg }}</h1>
    <div class="app-calculadora">
      <div class="display">0</div>
      <div class="botao">C</div>
      <div class="botao">+/-</div>
      <div class="botao">%</div>
      <div class="botao operadores">÷</div>
      <div class="botao">7</div>
      <div class="botao">8</div>
      <div class="botao">9</div>
      <div class="botao operadores">×</div>
      <div class="botao">4</div>
      <div class="botao">5</div>
      <div class="botao">6</div>
      <div class="botao operadores">−</div>
      <div class="botao">1</div>
      <div class="botao">2</div>
      <div class="botao">3</div>
      <div class="botao operadores">+</div>
      <div class="botao zero">0</div>
      <div class="botao">.</div>
      <div class="botao operadores">=</div>
    </div>    
  </div>
</template>

<script>
export default {
  name: 'Calculadora',
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

.app-calculadora{
  margin: 0 auto;
  width: 400px;
  font-size: 40px;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: minmax(50px, auto);
  font-family: FonteBody;
}

.display{
  grid-column: 1/5;
  background-color: black;
  color: white;
}

.zero{
  grid-column: 1/3;
}

.botao{
  background-color: #f2f2f2;
  border: 1px solid #999;
  cursor: pointer;
}

.botao:hover{
  background-color: #00F5FF;
}

.operadores{
  background-color: #FFF68F;
}  
</style>
