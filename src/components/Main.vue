<template>
  <main>
    <h3 class="text-center text-danger">{{ movieToSearch }}</h3>
    <FilmProfileCart />
  </main>
</template>

<script>
import axios from "axios";
import FilmProfileCart from "./FilmProfile.vue";
export default {
  name: "IndexMain",
  components: {
    FilmProfileCart,
  },
  data() {
    return {
      searchedFilms: [],
    };
  },
  props: ["movieToSearch"],
  updated() {
    // Ad ogni aggiornamento del data 'movieToSearch', richiamo il seguente metodo che aggiorna l'array list dei film ricercati
    this.getApiSearchedFilms(this.movieToSearch);
  },
  methods: {
    /* Il seguente metodo effettua una richiesta GET all'API, fornendo un input di ricerca. Aggiornerà quindi l'array dei film in base alla ricerca */
    getApiSearchedFilms(filmToSearch) {
      axios
        .get(
          `https://api.themoviedb.org/3/search/movie?api_key=f617480c0a93aca25c95f2b70e2824ca&query=${filmToSearch}`
        )
        .then((result) => {
          // Richiesta andata a buon fine
          // Inserisco il risultato della ricerca nell'array e stampo un messaggio a video
          this.searchedFilms = result.data.results;
          console.log("Recupero la lista dall'API");
        })
        .catch((error) => {
          // Errore nella richiesta
          console.log(error);
          console.log("errore");
        });
    },
  },
};
</script>

<style lang="scss" scoped>
</style>
