<template>
  <li>
    <ul class="py-4">
      <li>
        <img
          :src="`http://image.tmdb.org/t/p/w500/${movieObject.poster_path}`"
          :alt="`Image of ${movieObject.title}`"
          class="my-card-img"
        />
      </li>
      <li><span class="fw-bold">Titolo: </span>{{ movieObject.title }}</li>
      <li>
        <span class="fw-bold">Titolo Originale: </span
        >{{ movieObject.original_title }}
      </li>
      <li>
        <span class="fw-bold">Lingua: </span>
        <lang-flag :iso="movieObject.original_language" />
      </li>
      <li>
        <span class="fw-bold">Voto: </span>
        <i
          class="fas fa-star"
          v-for="(element, index) in 5"
          :key="index"
          :class="
            index < getIntegerVote(movieObject.vote_average) ? 'voted' : ''
          "
        ></i>
      </li>
    </ul>
  </li>
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
