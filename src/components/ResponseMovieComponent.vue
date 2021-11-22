<template>
  <div class="row justify-content-center py-5">
    <div class="col col-3" v-for="film in films" :key="film.id">
      <div class="card bg-dark mt-4">
        <div class="testo">
          <h4 class="text-center">{{ film.title }}</h4>
          <div class="title">
            <span>Titolo: {{ film.title }}</span>
          </div>
          <div class="original_title">
            <span>Titolo originale: {{ film.original_title }}</span>
          </div>
          <div class="lingua">
            <span
              >Lingua: {{ film.original_language }}
              <flag :iso="film.original_language" />
            </span>
          </div>
          <div class="voto">
            <i
              class="fas fa-star"
              v-for="icon in Math.round(film.vote_average / 2)"
              :key="icon"
            ></i>
            <i
              class="far fa-star"
              v-for="icon in 5 - Math.round(film.vote_average / 2)"
              :key="icon"
            ></i>
          </div>
        </div>
        <img
          :src="`https://image.tmdb.org/t/p/w342` + film.poster_path"
          alt=""
          class="image"
        />
      </div>
    </div>
    <hr class="text-light" />
    <div class="col col-3" v-for="tvSerie in tvSeries" :key="tvSerie.id">
      <div class="card bg-dark mt-4">
        <div class="testo">
          <h4 class="text-center">{{ tvSerie.name }}</h4>
          <div class="title">
            <span>Titolo: {{ tvSerie.name }}</span>
          </div>
          <div class="original_title">
            <span>Titolo originale: {{ tvSerie.original_name }}</span>
          </div>
          <div class="lingua">
            <span
              >Lingua: {{ tvSerie.original_language }}
              <flag :iso="tvSerie.original_language" />
            </span>
          </div>
          <div class="voto">
            <i
              class="fas fa-star"
              v-for="icon in Math.round(tvSerie.vote_average / 2)"
              :key="icon"
            ></i>
            <i
              class="far fa-star"
              v-for="icon in 5 - Math.round(tvSerie.vote_average / 2)"
              :key="icon"
            ></i>
          </div>
        </div>
        <img
          :src="`https://image.tmdb.org/t/p/w342` + tvSerie.poster_path"
          alt=""
          class="image"
        />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    films: Array,
    tvSeries: Array,
  },
};
</script>

<style lang="scss">
.col {
  .card {
    position: relative;
    .image {
      object-fit: cover;
      object-position: top;
      z-index: 2;
      &:hover {
        filter: opacity(0);
        transition: 1s;
      }
    }
    .testo {
      position: absolute;
      color: red;
    }
  }
}
</style>
