<template>
  <main class="container-fluid">
    <div class="row">
      <div class="col-12">
        <!-- <h3 class="text-center text-danger pt-5">
          {{ `Hai ricercato ${moviesSearched}` }}
        </h3> -->
        <ul>
          <FilmProfileCart
            v-for="(movie, index) in moviesSearched"
            :key="index"
            :movieObject="movie"
          />
        </ul>
      </div>
    </div>
  </main>
</template>

<script>
import FilmProfileCart from "./FilmProfile.vue";
export default {
  name: "IndexMain",
  components: {
    FilmProfileCart,
  },
  data() {
    return {
      currentPage: 1,
    };
  },
  props: ["moviesSearched"], //Array con la lista dei film filtrati
  methods: {},
};
</script>

<style lang="scss" scoped>
</style>
