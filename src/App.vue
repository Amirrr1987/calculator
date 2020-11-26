<template>
  <div id="app" class="app">
    <div class="calculator">
      <div id="result" class="calculator__item calculator--answer">{{ valueDisplayed }}</div>
      <button class="calculator__item calculator--decimal">.</button>
      <button class="calculator__item calculator--clean"   @click="clear">C</button>
      <button class="calculator__item calculator--divisi"  @click="handleOp('/')">/</button>
      <button class="calculator__item calculator--multi"   @click="handleOp('x')">*</button>
      <button class="calculator__item calculator--minus"   @click="handleOp('-')">-</button>
      <button class="calculator__item calculator--plus"    @click="handleOp('+')">+</button>
      <button class="calculator__item calculator--equal"   @click="handleOp('=')">=</button>
      <button class="calculator__item calculator--n0"      @click="handleDigit(0)">0</button>
      <button class="calculator__item calculator--n1"      @click="handleDigit(1)">1</button>
      <button class="calculator__item calculator--n2"      @click="handleDigit(2)">2</button>
      <button class="calculator__item calculator--n3"      @click="handleDigit(3)">3</button>
      <button class="calculator__item calculator--n4"      @click="handleDigit(4)">4</button>
      <button class="calculator__item calculator--n5"      @click="handleDigit(5)">5</button>
      <button class="calculator__item calculator--n6"      @click="handleDigit(6)">6</button>
      <button class="calculator__item calculator--n7"      @click="handleDigit(7)">7</button>
      <button class="calculator__item calculator--n8"      @click="handleDigit(8)">8</button>
      <button class="calculator__item calculator--n9"      @click="handleDigit(9)">9</button>
  </div>
</div>
</template>

<script>
  export default {
    name: 'App',
    data(){
      return{
       
      currentValue: 0,
      savedValue: false,
      currentOp: false
      }
    },
  methods: {
    clear () {
      this.currentValue = 0
      this.savedValue = false
      this.currentOp = false
    },
    handleDigit (digit) {
      if (this.currentOp === '=') {
        this.savedValue = false
      }
      this.currentValue = this.currentValue * 10 + digit
    },
    handleOp (op){
      if (this.currentOp) {
         this.process()
      }
      else {
        this.savedValue = this.currentValue
      }
      this.currentValue = 0
      this.currentOp = op      
    },
    process() {
      if (this.currentOp === '+') {
        this.savedValue += this.currentValue
      }
      else if (this.currentOp === '-') {
        this.savedValue -= this.currentValue
      }
      else if (this.currentOp === 'x') {
        this.savedValue *= this.currentValue
      }
      else if (this.currentOp === '/') {
        this.savedValue /= this.currentValue
      }
      else if (this.currentOp === '=' && this.currentValue) {
        this.savedValue = this.currentValue
      }
      this.currentValue = 0
      this.currentOp = false
    }
  },
  computed: {
     valueDisplayed () {
      return this.savedValue ? 
        this.currentValue ? 
        this.currentValue : this.savedValue
        : this.currentValue
    }
  }
  }
</script>

<style lang="scss">


*{
  margin: 0;
  padding: 0;
}
@function height($size: $width){
  @return $size * 1.7;
}
$width: 100vw;
$height: 100vh;
$main-color: #60627B;
button{
  cursor: pointer;
  border: none;
  outline: none;
  font-size: 1.2em;
  border:none;
  border-radius: 50px;
  height: 4.5rem;
  width : 4.5rem;
  &:active{
      border-radius: 34px;
      box-shadow: 3px 3px 0px $main-color;
      color: orange;
  }
}
.app{
  background-color: darken($main-color , 2%);
  width : $width;
  height: $height; 
  display: flex;
  justify-content: center;
  align-items: center;
}
.calculator {
  height: 90vh;
  width : 90vw;
  background-color: $main-color;
  display: grid;
  grid-template-columns: 1fr 1fr 1fr 1fr;
  grid-template-rows: 2fr 1fr 1fr 1fr 1fr 1fr 1fr;
  grid-template-areas:
    'answer answer answer answer'
    'answer answer answer answer'
    'clean division multiplication minus'
    'n7 n8 n9 plus'
    'n4 n5 n6 equal'
    'n1 n2 n3 equal'
    'n0 n0 decimal equal'
    ;
  gap: 13px;
    &__item {
      background-color: $main-color;
      display: flex;
      justify-content: center;
      align-items: center;
      color: #FFF;
      box-shadow: 3px 3px 11px #1e1f20, -2px -2px 10px rgb(151,147,147);
      font-size: 2rem;
    }

    &--answer {
      grid-area: answer;
      background-color: lighten($main-color, 10%);
      box-shadow: inset 0px 0px 4px #1e1f20, -2px -2px 10px #979393;
      word-wrap: break-word;
      // width: 100%;
      display: block;
      font-size: 3em;
      // justify-content: left;
      // align-items: baseline;
      padding: .5rem 1rem;
    }

    &--clean {
      grid-area: clean;
   }

    &--decimal {
      grid-area: decimal;
   }

    &--division {
      grid-area: division;
    }

    &--equal {
      grid-area: equal;
      height: 100%;
   }

    &--minus {
      grid-area: minus;
    }

    &--multiplication {
      grid-area: multiplication;
    }

    &--n0 {
      grid-area: n0;
      width: 100%;
    }
  
    &--n1 {
      grid-area: n1;
    }

    &--n2 {
      grid-area: n2;
    }

    &--n3 {
      grid-area: n3;
    }

    &--n4 {
      grid-area: n4;
    }

    &--n5 {
      grid-area: n5;
    }

    &--n6 {
      grid-area: n6;
    }

    &--n7 {
      grid-area: n7;
    }

    &--n8 {
      grid-area: n8;
    }

    &--n9 {
      grid-area: n9;
    }

    &--plus {
      grid-area: plus;
    }
}
</style>