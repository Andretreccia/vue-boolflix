<template>
  <div>
    <input v-model="userInput" type="text" placeholder="cerca un film" />
    <button @click="callSearch">search</button>
    <div class="container">
      <div class="row justify-content-center py-5">
        <div class="col col-5" v-for="film in films" :key="film.qualcosa">
          <div class="card p-3">
            <h4 class="text-center">Film:</h4>
            <div class="title">
              <span>Titolo: {{ film.title }}</span>
            </div>
            <div class="original_title">
              <span>Titolo originale: {{ film.original_title }}</span>
            </div>
            <div class="lingua">
              <span>Lingua: {{ film.original_language }}</span>
            </div>
            <div class="voto">
              <span>Voto: {{ film.vote_average }}</span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
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