<script setup>
  import { ref, computed } from 'vue';

  const name = 'vue dinámico'

  const counter = ref(0)
  const arrayFavs = ref([])

  // Metodo - Methods
  const increment = () => {
    counter.value++
  }

  const decrease = () => counter.value--

  const rest = () => counter.value = 0

  const add = () => { 
    arrayFavs.value.push(counter.value)
  }

  // Propiedades computadas
  const classCounter = computed (() => {
    if (counter.value === 0) {
      return 'zero'
    }
    if (counter.value > 0) {
      return 'positive'
    }
    if (counter.value < 0) {
      return 'negative'
    }
  })

  const bloqueaBtnAdd = computed(() => {
    // num es cada elemento del array, si num es igual counter retorna el número
    const numSearch = arrayFavs.value.find((num) => num === counter.value)
    // console.log(numSearch)
    // if (numSearch === 0) return true
    // return numSearch ? true : false
    return numSearch || numSearch === 0
  })
</script>

<template>
  <div class="container text-center mt-3">
    <h1>Hola {{ name.toUpperCase() }}</h1>
    <!-- <h2 :class="counter > 0 ? 'positive' : 'negative' ">{{ counter }}</h2> -->
    <h2 :class="classCounter">{{ counter }}</h2>
    <div class="btn-group">
      <button @click="increment" class="btn btn-success">Aumentar</button>
      <button @click="rest" class="btn btn-danger">Reiniciar</button>
      <button @click="decrease" class="btn btn-secondary">Disminuir</button>
      <button @click="add" :disabled="bloqueaBtnAdd" class="btn btn-primary">Add</button>
    </div>
    <ul class="list-group mt-4">
      <li 
        class="list-group-item"
        v-for="(num, index) in arrayFavs" 
        :key="index"
      >
        {{ num }}
      </li>
    </ul>
  </div>
</template>

<style>
  h1 {
    color: red;
  }
  .positive {
    color: green;
  }
  .negative {
    color: red;
  }
  .zero {
    color: black;
  }
</style>