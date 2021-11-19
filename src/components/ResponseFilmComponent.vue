<template>
  <div class="row justify-content-center py-5">
    <div class="col col-5" v-for="film in films" :key="film.id">
      <div class="card p-3 bg-dark bg-opacity-10 mt-4">
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
        <div
          class="voto"
          v-for="icon in Math.round(film.vote_average / 2)"
          :key="icon"
        >
          <i class="fas fa-star"></i>
        </div>
        <div
          class="voto"
          v-for="icon in 5 - Math.round(film.vote_average / 2)"
          :key="icon"
        >
          <i class="far fa-star"></i>
        </div>
        <div class="image">
          <img
            :src="`https://image.tmdb.org/t/p/w200` + film.poster_path"
            alt=""
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    films: Array,
  },
};
</script>

<style lang="scss">
</style>
