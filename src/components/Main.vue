<template>
  <main class="container">
    <div class="row pt-4 pb-2">
      <div class="col-12">
        <h2 v-if="userSearch != ''">Risultati per {{ userSearch }}...</h2>
        <h2 v-else>Ricerca un Film o una Serie TV</h2>
      </div>
    </div>
    <div
      class="
        row row-cols-1 row-cols-sm-2 row-cols-md-3 row-cols-lg-4 row-cols-xl-5
        g-4
        pb-5
      "
    >
      <FilmProfileCart
        v-for="(movie, index) in moviesSearched"
        :key="index"
        :movieObject="movie"
      />
    </div>
    <div class="row pt-1 pb-2" v-show="seriesSearched.length > 0">
      <div class="col-12">
        <h2>Serie TV</h2>
      </div>
    </div>
    <div
      class="
        row row-cols-1 row-cols-sm-2 row-cols-md-3 row-cols-lg-4 row-cols-xl-5
        g-4
        pb-5
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
    userSearch: String, //Stringa contenente il risultato della ricerca dell'utente
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
    width: 100%;
    height: 100%;
    object-fit: cover;
    color: black;
  }

  .my-card-body {
    display: none;
    position: absolute;
    top: 0;
    width: 100%;
    height: 100%;
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
