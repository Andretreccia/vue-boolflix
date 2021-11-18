<template>
  <div>
    <div class="d-flex justify-content-center">
      <h2 class="me-5">Cerca film nei nostri archivi:</h2>
      <input v-model="userInput" type="text" placeholder="cerca un film" />
      <button @click="callSearch">search</button>
    </div>
    <div class="container">
      <ResponseFilmComponent :films="films" />
    </div>
  </div>
</template>

<script>
import axios from "axios";
import ResponseFilmComponent from "./ResponseFilmComponent.vue";
export default {
  components: {
    ResponseFilmComponent,
  },
  data() {
    return {
      films: [],
      loading: false,
      apiKey: "cde5362f29f305e58d2e01a906c2d55",
      userInput: "",
    };
  },
  mounted() {},
  methods: {
    callSearch() {
      axios
        .get(
          "https://api.themoviedb.org/3/search/movie?api_key=" +
            this.apiKey +
            "e&language=en-US&query=" +
            this.userInput +
            "&page=1&include_adult=false"
        )
        .then((r) => {
          this.films = r.data.results;
          this.loading = true;
        })
        .catch((e) => {
          console.log(e, "Non funge");
        });
      console.log(this.film);
    },
  },
};
</script>

<style lang="scss">
</style>