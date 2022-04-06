<template>
  <div class="col">
    <div class="card h-100">
      <img
        :src="`http://image.tmdb.org/t/p/w500/${serieObject.poster_path}`"
        :alt="`Image of ${serieObject.name}`"
        class="card-img-top"
      />
      <div class="my-card-body px-2 py-3">
        <h6><span class="fw-bold">Titolo: </span>{{ serieObject.name }}</h6>
        <h6>
          <span class="fw-bold">Titolo Originale: </span
          >{{ serieObject.original_name }}
        </h6>
        <h6>
          <span class="fw-bold">Lingua: </span>
          <lang-flag :iso="serieObject.original_language" />
        </h6>
        <span class="fw-bold">Voto: </span>
        <i
          class="fas fa-star"
          v-for="(element, index) in 5"
          :key="index"
          :class="
            index < getIntegerVote(serieObject.vote_average) ? 'voted' : ''
          "
        ></i>
        <p class="my-card-description">
          <span class="fw-bold">Overview: </span>
          {{ serieObject.overview }}
        </p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "SeriesCart",
  data() {
    return {};
  },
  props: ["serieObject"],
  methods: {
    getIntegerVote(vote) {
      return Math.floor(vote / 2);
    },
  },
};
</script>

<style lang="scss" scoped>
</style>
