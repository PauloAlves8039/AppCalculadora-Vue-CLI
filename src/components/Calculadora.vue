<template>
  <div class="calculadora">
    <h1>{{ msg }}</h1>
    <div class="app-calculadora">
      <div class="display">{{ valorCorrente || '0'}}</div>
      <div @click="limpar" class="botao">C</div>
      <div @click="sinal" class="botao">+/-</div>
      <div @click="porcentagem" class="botao">%</div>
      <div @click="dividir" class="botao operadores">÷</div>
      <div @click="obterNumero('7')" class="botao">7</div>
      <div @click="obterNumero('8')" class="botao">8</div>
      <div @click="obterNumero('9')" class="botao">9</div>
      <div @click="multiplicar" class="botao operadores">×</div>
      <div @click="obterNumero('4')" class="botao">4</div>
      <div @click="obterNumero('5')" class="botao">5</div>
      <div @click="obterNumero('6')" class="botao">6</div>
      <div @click="subtrair" class="botao operadores">−</div>
      <div @click="obterNumero('1')" class="botao">1</div>
      <div @click="obterNumero('2')" class="botao">2</div>
      <div @click="obterNumero('3')" class="botao">3</div>
      <div @click="somar" class="botao operadores">+</div>
      <div @click="obterNumero('0')" class="botao zero">0</div>
      <div @click="ponto" class="botao">.</div>
      <div @click="resultado" class="botao operadores">=</div>
    </div>    
  </div>
</template>

<script>
export default {
  name: 'Calculadora',
  props: {
    msg: String
  },
  data(){
    return{
      valorCorrente: '',
      numeroanterior: null,
      operador: null,
      operadorClicado: false
    }
  },
  methods: {
    /**
    *  Função resposável por limpar o display da calculadora. 
    */
    limpar(){
      this.valorCorrente = ''
    },

    /**
    *  Função resposável por atribuir sinal de + ou - para cálculos operacionais. 
    */
    sinal(){
      this.valorCorrente =this.valorCorrente.charAt(0) === '-' 
        ? this.valorCorrente.slice(1)
        : `-${this.valorCorrente}`

    },

    /**
     * Função responsável pelo cálculo da porcentagem.
     */
    porcentagem(){
      this.valorCorrente = `${parseFloat(this.valorCorrente) / 100}` 
    },

    /**
     * Função responsável por obter os números no display. 
     */
    obterNumero(num){
      if(this.operadorClicado){
        this.valorCorrente = ''
        this.operadorClicado = false
      }
      this.valorCorrente = `${this.valorCorrente}${num}` 
    },

    /**
     * Função responsável por adicionar ponto no display. 
     */
    ponto(){
      if(this.valorCorrente.indexOf('.') === -1){
        this.obterNumero('.')
      }
    },

    /**
     * Função responsável por atribuir valores no display. 
     */
    setarValor(){
      this.numeroanterior = this.valorCorrente
      this.operadorClicado = true
    },

    /**
     * Função responsável pela operação de divisão. 
     */
    dividir(){
      this.operador = (num1, num2) => num1 / num2
      this.setarValor()
    },

    /**
     * Função responsável pela operação de multiplicação. 
     */
    multiplicar(){
      this.operador = (num1, num2) => num1 * num2
      this.setarValor()
    },

    /**
     * Função responsável pela operação de subtração. 
     */
    subtrair(){
      this.operador = (num1, num2) => num1 / num2
      this.setarValor()
    },

    /**
     * Função responsável pela operação de soma. 
     */
    somar(){
      this.operador = (num1, num2) => num1 + num2
      this.setarValor()
    },

    /**
     * Função responsável pela exibição dos resultados das operações.
     */
    resultado(){
      this.valorCorrente = `${this.operador(
        parseFloat(this.numeroanterior),
        parseFloat(this.valorCorrente)
      )}`
      this.numeroanterior = null
    }
  },
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
