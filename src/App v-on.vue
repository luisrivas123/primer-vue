<script setup>
  const name = 'vue dinámico'

  // Metodo - Methods

  const handleClick1 = () => {
    console.log('me diste click');
  }
  const handleClick2 = (message) => {
    console.log(message);
  }

</script>

<template>
  <h1>Hola {{ name.toUpperCase() }}</h1>
  <button v-on:click="handleClick1">Activame-1</button>
  <button @click.right.prevent="handleClick2('Texto Right')">Activame right</button>
  <button @click="handleClick2('Texto Left')">Activame left</button>
  <button @click.middle="handleClick2('Texto Middle')">Activame middle</button>
</template>

<style>
  h1 {
    color: red;
  }
</style>