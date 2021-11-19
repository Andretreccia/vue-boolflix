<template>
  <div>
    <div class="d-flex justify-content-center">
      <h2 class="me-5">Cerca film nei nostri archivi:</h2>
      <input v-model="userInput" type="text" placeholder="cerca un film" />
      <button @click="callSearch">search</button>
    </div>
    <div class="container">
      film
      <ResponseFilmComponent :films="films" />
      <hr />
      <hr />
      serie tv
      <ResponseTvComponent :tvSeries="tvSeries" />
    </div>
  </div>
</template>

<script>
import axios from "axios";
import ResponseFilmComponent from "./ResponseFilmComponent.vue";
import ResponseTvComponent from "./ResponseTvComponent.vue";
export default {
  components: {
    ResponseFilmComponent,
    ResponseTvComponent,
  },
  data() {
    return {
      films: [],
      tvSeries: [],
      apiKey: "cde5362f29f305e58d2e01a906c2d55",
      userInput: "",
    };
  },
  mounted() {},
  methods: {
    callSearch() {
      let reqMovie =
        "https://api.themoviedb.org/3/search/movie?api_key=" +
        this.apiKey +
        "e&language=en-US&query=" +
        this.userInput; /* +
        "&page=1&include_adult=false" */

      let reqTv =
        "https://api.themoviedb.org/3/search/tv?api_key=" +
        this.apiKey +
        "e&language=en-US&query=" +
        this.userInput; /* +
        "&page=1&include_adult=false" */
      const rOne = axios.get(reqMovie);
      const rTwo = axios.get(reqTv);
      axios
        .all([rOne, rTwo])
        .then(
          axios.spread((...r) => {
            this.films = r[0].data.results;
            this.tvSeries = r[1].data.results;
            console.log(this.tvSeries);
          })
        )
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