<template>
  <li>
    <ul class="py-4">
      <li><span class="fw-bold">Titolo </span>{{ movieObject.title }}</li>
      <li>
        <span class="fw-bold">Titolo Originale </span
        >{{ movieObject.original_title }}
      </li>
      <li>
        <span class="fw-bold">Lingua </span>{{ movieObject.original_language }}
      </li>
      <li><span class="fw-bold">Voto </span>{{ movieObject.vote_average }}</li>
    </ul>
  </li>
</template>

<script>
export default {
  name: "FilmProfileCart",
  props: ["movieObject"],
};
</script>

<style lang="scss" scoped>
</style>
