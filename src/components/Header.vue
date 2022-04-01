<template>
  <header>
    <!-- L'utente inserisce un film da ricercare, alla pressione del tasto di invio, viene inviato il risultato della ricerca (inputSearch) sul canale 'userSearch' -->
    <input
      type="text"
      placeholder="Inserisci il titolo del film da ricercare"
      v-model="inputSearch"
      @keyup.enter="$emit('userSearch', inputSearch.trim())"
    />
  </header>
</template>

<script>
export default {
  name: "IndexHeader",
  data() {
    return {
      inputSearch: "",
    };
  },
};
</script>

<style lang="scss" scoped>
header {
  height: 100px;
  background-color: rgb(196, 108, 108);
}
</style>
