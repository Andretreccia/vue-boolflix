<template>
  <header>
    <div>
      <h1>BOOLFLIX</h1>
    </div>
    <div class="d-flex justify-content-center">
      <h2 class="me-5">Cerca film nei nostri archivi:</h2>
      <input v-model="userInput" type="text" placeholder="cerca un film" />
      <button @click="$emit('inputSearch', userInput)">search</button>
    </div>
  </header>
</template>

<script>
export default {
  data() {
    return {
      userInput: "",
    };
  },
};
</script>

<style lang="scss">
</style>