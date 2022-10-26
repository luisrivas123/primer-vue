<script setup>
  const name = 'vue dinámico'
  const styleColor = 'color: blue'
  const arrayColors = ['blue', 'red', 'black']
  const activo = false
  const arrayfruits = [
    {
      name: "Manzana",
      price: "$1.00",
      description: "Una manzana",
      stock: 0,
      id: 1
    },
    {
      name: "Pera",
      price: "$2.00",
      description: "Una Pera",
      stock: 10,
      id: 2
    },
    {
      name: "Naranja",
      price: "$3.00",
      description: "Una Naranja",
      stock: 20,
      id: 3
    }
  ]
  const objectFruits = {
    name: "Manzana",
    price: "$1.00",
    description: "Una manzana",
    id: 1
  }
</script>

<template>
  <h1>Hola {{ name.toUpperCase() }}</h1>
  <h2>{{}}</h2>
  <!-- <h2 v-bind:style="styleColor">Soy azúl</h2> -->
  <h2 v-bind:style="`color: ${arrayColors[1]}`">Soy azúl</h2>
  <!-- <h2>
    {{ activo ? 'Estoy activo' : 'Estoy inactivo' }}
  </h2> -->

  <h2 v-if="activo === true">Estoy activo</h2>
  <p v-else-if="activo === false">Estoy inactivo</p>
  <p v-else>Estoy indeciso</p>

  <h2 v-show="activo">Estoy activo</h2>

  <!-- <ul>
    <li
      v-for="(fruta, index) in arrayColors"
      :key="index"
    >
      {{ index }} - {{ fruta }}
    </li>
  </ul> -->

  <!-- <ul>
    <li
      v-for="fruta in arrayfruits"
      :key="fruta.id"
    >
      {{ fruta.name }}
      <ul>
        <li>
          {{ fruta.price }}
        </li>
        <li>
          {{ fruta.description }}
        </li>
      </ul>
    </li>
  </ul> -->

  <!-- <ul>
    <li
      v-for="(value, propiedad, index) of objectFruits"
      :key="value"
    >
      {{ index }} - {{ propiedad }}: {{ value }}
    </li>
  </ul> -->

  <ul>
    <template v-for="item in arrayfruits" :key="item.name">
      <li v-if="item.stock > 0">
        {{ item.name }} - {{ item.price }}
      </li>
    </template>
  </ul>

</template>

<style>
  h1 {
    color: red;
  }
</style>