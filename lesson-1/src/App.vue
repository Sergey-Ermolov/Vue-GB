<template>
  <div>
    <input type="number" v-model="a">
    <input type="number" v-model="b">

    <p>Результат: {{ result }}</p>
    
    <button v-on:click="result = Number(a) + Number(b)">Сложение</button>
    <button v-on:click="result = Number(a) - Number(b)">Вычитание</button>
    <button v-on:click="result = Number(a) * Number(b)">Умножение</button>
    <button v-on:click="result = Number(a) / Number(b)">Деление</button>
    <button v-on:click="result = Math.floor(a/b)">Целочисленное деление</button>
    <button v-on:click="result = Math.pow(a, b)">Возведение в степень</button>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      a: 0,
      b: 0,
      result: 0
    }
  }
}
</script>

<style lang="scss">
button {
  height: 30px;
  background: rgb(89, 149, 226);
  margin-left: 4px;
  color: rgb(5, 46, 61);
  border-color: rgb(58, 30, 181);
  border-radius: 5px;
}
button:hover {
  background: rgb(5, 46, 61);
  color: rgb(89, 149, 226);
  cursor: pointer;
}
</style>
