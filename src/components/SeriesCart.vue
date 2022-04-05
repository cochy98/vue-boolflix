<template>
  <li>
    <ul class="py-4">
      <li>
        <img
          :src="`http://image.tmdb.org/t/p/w500/${serieObject.poster_path}`"
          :alt="`Image of ${serieObject.name}`"
          class="my-card-img"
        />
      </li>
      <li><span class="fw-bold">Titolo </span>{{ serieObject.name }}</li>
      <li>
        <span class="fw-bold">Titolo Originale </span
        >{{ serieObject.original_name }}
      </li>
      <li>
        <span class="fw-bold">Lingua </span>
        <lang-flag :iso="serieObject.original_language" />
      </li>
      <li><span class="fw-bold">Voto </span>{{ serieObject.vote_average }}</li>
    </ul>
  </li>
</template>

<script>
export default {
  name: "SeriesCart",
  data() {
    return {};
  },
  props: ["serieObject"],
  methods: {},
};
</script>

<style lang="scss" scoped>
</style>
