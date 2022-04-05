<template>
  <main class="container">
    <div
      class="
        row row-cols-1 row-cols-sm-2 row-cols-md-3 row-cols-lg-4 row-cols-xl-5
        g-4
        py-5
      "
    >
      <FilmProfileCart
        v-for="(movie, index) in moviesSearched"
        :key="index"
        :movieObject="movie"
      />
    </div>
    <h3 class="text-center text-danger pt-5">TV Series</h3>
    <div
      class="
        row row-cols-1 row-cols-sm-2 row-cols-md-3 row-cols-lg-4 row-cols-xl-5
        g-4
        py-5
      "
    >
      <SeriesCart
        v-for="(serie, index) in seriesSearched"
        :key="index"
        :serieObject="serie"
      />
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
.card {
  border: none !important;
  border-radius: 0 !important;

  img.card-img-top {
    border-top-left-radius: 0;
    border-top-right-radius: 0;
  }

  .my-card-body {
    display: none;
    position: absolute;
    top: 0;
    width: 100%;
    height: 100%;
    /* border: 2px solid red; */
    background-color: rgba(0, 0, 0, 0.8);
    overflow-y: auto;

    i.fa-star {
      color: rgb(170, 169, 169);
    }

    i.fa-star.voted {
      color: rgb(255, 222, 35);
    }

    /* p.my-card-description {
    } */
  }
}

.card:hover .my-card-body {
  display: block;
}
</style>
