<script setup lang="ts">
import { computed, reactive, ref, toRefs, watch } from 'vue';

const name2 = "chair"
const price2 = 3500
const url = "https://example.com"

const item1 = reactive({
  name: "desk",
  price: 2000,
})

const budget = 50000

const priceLabel = ref<string>(item1.price + "yen")
const { price } = toRefs(item1)
watch(price, () => {
  if (price.value > budget * 2) priceLabel.value = "tooooo"
  else if (price.value > budget) priceLabel.value = "MAA"
  else priceLabel.value = price.value + "yen"
})

const buy = (name: string) => alert(`buy ${name}`)

const clear = () => {
  item1.name = ''
  item1.price = 0
}
</script>

<template>
<div class="container">
  <h1>最近の支出</h1>
  <input v-model="item1.name"/>
  <input v-model="item1.price"/>
  <button v-on:click="clear">Clear</button>
  <div class="payment">
    <label>{{ item1.name }}</label>
    <label>{{ priceLabel }}</label>
    <a v-bind:href="url">url</a>
    <button v-on:click="buy(item1.name)">buy</button>
  </div>
  <div class="payment">
    <label>{{ name2 }}</label>
    <label>{{ price2 }}</label>
    <button v-on:click="buy(name2)">buy</button>
  </div>
</div>
</template>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
}
.payment {
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 80px;
  width: 400px;
  background-color: aliceblue;
  margin-bottom: 1rem;
}
input {
  margin-bottom: 1rem;
}
label {
  font-weight: bold;
  font-size: 20px;
}
</style>