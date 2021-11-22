<template>
  <div id="app" class="bg-dark">
    <SiteHeader @inputSearch="callSearch" />
    <SiteMain :films="films" :tvSeries="tvSeries" />
  </div>
</template>

<script>
import axios from "axios";
import SiteHeader from "./components/SiteHeader.vue";
import SiteMain from "./components/SiteMain.vue";
export default {
  name: "App",
  components: {
    SiteHeader,
    SiteMain,
  },
  data() {
    return {
      films: [],
      tvSeries: [],
      apiKey: "cde5362f29f305e58d2e01a906c2d55",
    };
  },
  methods: {
    callSearch(userInput) {
      let reqMovie =
        "https://api.themoviedb.org/3/search/movie?api_key=" +
        this.apiKey +
        "e&language=en-US&query=" +
        userInput; /* +
        "&page=1&include_adult=false" */

      let reqTv =
        "https://api.themoviedb.org/3/search/tv?api_key=" +
        this.apiKey +
        "e&language=en-US&query=" +
        userInput; /* +
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
@import "../node_modules/bootstrap/scss/bootstrap.scss";
</style>
