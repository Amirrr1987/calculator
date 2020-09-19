<template>
  <body id="app">
    <div class="calculator">
    <div class="calculator__item calculator--answer"></div>
    <button class="calculator__item calculator--clean">C</button>
    <button class="calculator__item calculator--division">/</button>
    <button class="calculator__item calculator--multiplication">*</button>
    <button class="calculator__item calculator--minus">-</button>
    <button class="calculator__item calculator--plus">+</button>
    <button class="calculator__item calculator--equal">=</button>
    <button class="calculator__item calculator--decimal">.</button>
    <button class="calculator__item calculator--n0">0</button>
    <button class="calculator__item calculator--n1">1</button>
    <button class="calculator__item calculator--n2">2</button>
    <button class="calculator__item calculator--n3">3</button>
    <button class="calculator__item calculator--n4">4</button>
    <button class="calculator__item calculator--n5">5</button>
    <button class="calculator__item calculator--n6">6</button>
    <button class="calculator__item calculator--n7">7</button>
    <button class="calculator__item calculator--n8">8</button>
    <button class="calculator__item calculator--n9">9</button>
  </div>
  </body>
</template>
<script>
export default {
  name: 'App',

}
</script>

<style lang="scss">
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
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
  &:active{
      border-radius: 4px;
      box-shadow: 3px 3px 0px $main-color;
      color: orange;
  }
}
#app{
  background-color: darken($main-color , 2%);
  width : $width;
  height: $height;  
  display: flex;
  justify-content: center;
  align-items: center;
  // padding: 10px;
}
.calculator {
  height: 90%;
  width : 90%;
  background-color: $main-color;
  display: grid;
  grid-template-columns: 1fr 1fr 1fr 1fr;
  grid-template-rows: repeat(7,1fr);
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
    }

    &--answer {
      grid-area: answer;
      background-color: lighten($main-color, 10%);
      box-shadow: inset 0px 0px 4px #1e1f20, -2px -2px 10px #979393;
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
   }

    &--minus {
      grid-area: minus;
    }

    &--multiplication {
      grid-area: multiplication;
    }

    &--n0 {
      grid-area: n0;
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