<template>
  <header id="site-header" class="position-fixed w-100">
    <nav class="navbar navbar-light bg-dark justify-content-between">
      <a class="navbar-brand text-light ms-5">BOOLFIX</a>
      <form class="d-flex me-5" v-on:submit.prevent>
        <input
          class="form-control mr-sm-2 bg-dark text-light"
          type="search"
          placeholder="cerca un film"
          v-model="userInput"
        />
        <button
          class="btn btn-primary my-2 my-sm-0 bg-dark border-light m-1"
          type="submit"
          @click="$emit('inputSearch', userInput)"
        >
          Search
        </button>
      </form>
    </nav>
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
#site-header {
  z-index: 100;
}
</style>