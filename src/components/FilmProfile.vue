<template>
  <div class="col">
    <div class="card h-100">
      <img
        :src="`http://image.tmdb.org/t/p/w500/${movieObject.poster_path}`"
        :alt="`Image of ${movieObject.title}`"
        class="card-img-top"
      />
      <div class="my-card-body px-2 py-3">
        <h6><span class="fw-bold">Titolo: </span>{{ movieObject.title }}</h6>
        <h6>
          <span class="fw-bold">Titolo Originale: </span
          >{{ movieObject.original_title }}
        </h6>
        <h6>
          <span class="fw-bold">Lingua: </span>
          <lang-flag :iso="movieObject.original_language" />
        </h6>
        <span class="fw-bold">Voto: </span>
        <i
          class="fas fa-star"
          v-for="(element, index) in 5"
          :key="index"
          :class="
            index < getIntegerVote(movieObject.vote_average) ? 'voted' : ''
          "
        ></i>
        <p class="my-card-description">
          <span class="fw-bold">Overview: </span>
          {{ movieObject.overview }}
        </p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "FilmProfileCart",
  data() {
    return {};
  },
  props: ["movieObject"],
  methods: {
    getIntegerVote(vote) {
      return Math.floor(vote / 2);
    },
  },
};
</script>

<style lang="scss" scoped>
</style>
