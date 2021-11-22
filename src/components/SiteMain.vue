<template>
  <main class="bg-dark">
    <div class="container">
      <ResponseMovieComponent :films="films" :tvSeries="tvSeries" />
      <hr />
      <hr />
      <!-- serie tv
      <ResponseTvComponent :tvSeries="tvSeries" /> -->
    </div>
  </main>
</template>

<script>
import ResponseMovieComponent from "./ResponseMovieComponent.vue";
//import ResponseTvComponent from "./ResponseTvComponent.vue";
export default {
  components: {
    ResponseMovieComponent,
    //ResponseTvComponent,
  },
  props: {
    tvSeries: Array,
    films: Array,
  },
  mounted() {},
  methods: {},
};
</script>

<style lang="scss">
</style>