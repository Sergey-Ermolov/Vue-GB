<template>
  <div>
    <input type="number" v-model="a" v-on:change="checkInput(1)">
    <input type="number" v-model="b" v-on:change="checkInput(2)">

    <div class="radio-button">
      <label for="one"><input type="radio" id="one" value="Первый импут" v-model="radioButton">Первый импут</label>
      <br>
      <label for="two"><input type="radio" id="two" value="Второй импут" v-model="radioButton">Второй импут</label>
      <br>
    </div>

    <p> Выбран: {{ radioButton }}</p>

    <p>Результат: {{ result }}</p>
    
    <button v-on:click="summ">Сложение</button>
    <button v-on:click="sub">Вычитание</button>
    <button v-on:click="mult">Умножение</button>
    <button v-on:click="split">Деление</button>
    <button v-on:click="intSplit">Целочисленное деление</button>
    <button v-on:click="exponent">Возведение в степень</button>

    <label class="checkbox"><input type="checkbox" id="checkbox" v-model="checked">Отобразить клавиатуру</label>
    
 
    <div v-if="checked" class="keyboard">
      <button v-for="item of keyboardButton" v-on:click="keyDown(item)" v-bind:key="item">{{ item }}</button>
      <button v-on:click="del">Del</button>
    </div>

  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      a: 0,
      b: 0,
      result: 0,
      checked: false,
      keyboardButton: [
        '0',
        '1',
        '2',
        '3',
        '4',
        '5',
        '6',
        '7',
        '8',
        '9',
      ],
      radioButton: '',
      currentEnter: 1
    }
  },
  methods: {
    keyDown(item) {
      if(this.currentEnter == 1) {
        this.a = this.a == 0 ? '' : this.a
        this.a = String(this.a) + String(this.item)
      } else (this.currentEnter == 2) 
      {
        this.b = this.b == 0 ? '' : this.b
        this.b = String(this.b) + String(this.item)
      }
    },
    activRadioButton(id) {
      this.radioButton = id
    },
    del () {
      if(this.currentEnter == 1) {
        this.a = this.a.slise(0, -1)
        this.a = this.a == '' ? 0 : this.a
      } else (this.currentEnter == 2) 
      {
        this.b = this.b.slise(0, -1)
        this.b = this.b == '' ? 0 : this.b
      }
    },
    checkInput(numberInput) {
      this.currentEnter == numberInput
    },
    summ() {
      this.result = Number(this.a) + Number(this.b)
    },
    sub() {
      this.result = Number(this.a) - Number(this.b)
    },
    mult() {
      this.result = Number(this.a) * Number(this.b)
    },
    split() {
      this.result = Number(this.a) / Number(this.b)
    },
    intSplit() {
      this.result = Math.floor(this.a/this.b)
    },
    exponent() {
      this.result = Math.pow(this.a, this.b)
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

.checkbox {
  display: block;
  margin-top: 20px;
  width: 100%;
}

.keyboard {
  margin-top: 20px;
  margin: 20px;
}

.radio-button {
  margin-top: 20px;
}
</style>
