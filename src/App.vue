<template>
  <div id="app">
    <Header @query= "getApi" />
    <Main :cards= "cards"/>
  </div>
</template>

<script>
import axios from "axios"
import Header from "./components/Header"
import Main from "./components/Main"

export default {
  name: 'App',
  components: {
    Header,
    Main
  },
  data () {
    return {
      apiUrl: "https://api.themoviedb.org/3/search/movie",
      myApyKey: "c8d84c5c4b83aa407def8990d5ce320f",
      query: "",
      lenguage: "it-IT",
      cards: null // è un array che contiene gli oggetti "cards" (cioè i film)
    }
  },
  computed: {
  },
  methods: {
    takeQueryFromHeader(query) {
      this.query = query
    },
    getApi(query) {
      this.takeQueryFromHeader(query);
      axios
        .get (this.apiUrl + "?api_key=" + this.myApyKey + "&query=" + this.query + "&language=" + this.lenguage)
        .then ((result) => {
          this.cards = result.data.results;

          // this.dischi.forEach((disco) => {
          //     if (!this.genres.includes(disco.genre)) {
          //         this.genres.push(disco.genre);
          //     }
          // });
        })
        .catch((errore) => {
            alert(errore);
        });
    }
  }
}
</script>

<style lang="scss">
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }
  #app {
    height: 100vh;
    font-family: Avenir, Helvetica, Arial, sans-serif;
  }
</style>