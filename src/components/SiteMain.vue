<template>
  <div>
    <input v-model="userInput" type="text" placeholder="cerca un film" />
    <button @click="debugFunction">search</button>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      film: [],
      loading: false,
      apiKey: "cde5362f29f305e58d2e01a906c2d55",
      userInput: "",
    };
  },
  mounted() {
    this.callFilmApi();
  },
  methods: {
    callFilmApi() {},

    debugFunction() {
      axios
        .get(
          "https://api.themoviedb.org/3/search/movie?api_key=" +
            this.apiKey +
            "e&language=en-US&query=" +
            this.userInput +
            "&page=1&include_adult=false"
        )
        .then((r) => {
          this.film = r.data.results;
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