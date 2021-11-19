<template>
  <div class="row justify-content-center py-5">
    <div class="col col-5" v-for="tvSerie in tvSeries" :key="tvSerie.id">
      <div class="card p-3 bg-dark bg-opacity-10 mt-4">
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
          <span>Voto: {{ tvSerie.vote_average }}</span>
        </div>
        <div class="image">
          <img
            :src="`https://image.tmdb.org/t/p/w200` + tvSerie.poster_path"
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
    tvSeries: Array,
  },
};
</script>

<style lang="scss">
</style>
