<template>
  <main class="container-fluid">
    <div class="row">
      <div class="col-12">
        <h3 class="text-center text-danger pt-5">Movie</h3>
        <ul>
          <FilmProfileCart
            v-for="(movie, index) in moviesSearched"
            :key="index"
            :movieObject="movie"
          />
        </ul>
      </div>
      <div class="col-12">
        <h3 class="text-center text-danger pt-5">TV Series</h3>
        <ul>
          <SeriesCart
            v-for="(serie, index) in seriesSearched"
            :key="index"
            :serieObject="serie"
          />
        </ul>
      </div>
    </div>
  </main>
</template>

<script>
import FilmProfileCart from "./FilmProfile.vue";
import SeriesCart from "./SeriesCart.vue";

export default {
  name: "IndexMain",
  components: {
    FilmProfileCart,
    SeriesCart,
  },
  data() {
    return {
      currentPage: 1,
    };
  },
  props: {
    moviesSearched: Array, //Array con la lista dei film filtrati
    seriesSearched: Array, //Array con la lista delle serie filtrati
  },
  methods: {},
};
</script>

<style lang="scss">
li {
  img.my-card-img {
    width: 200px;
  }

  i.fa-star {
    color: rgb(170, 169, 169);
  }

  i.fa-star.voted {
    color: rgb(255, 222, 35);
  }
}
</style>
