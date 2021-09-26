<template>
  <div id="app">
    <Header @query= "trigger" />
    <Main
    :query= "query"
    :totalResults= "totalResults"
    :cards= "cards"
    :loading= "loading"
    />
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
      lenguage: "it-IT",
      query: "",
      totalResults: null,
      cards: [],
      loading: false
    }
  },
  methods: {
    trigger(query) {
      this.query = query;
      this.getApiData();
    },
    getApiData() {
      if (this.query != "") {
        this.loading = true;
        axios
          .get (this.apiUrl + "?api_key=" + this.myApyKey + "&query=" + this.query + "&language=" + this.lenguage)
          .then ((result) => {
            this.totalResults = result.data.total_results;
            if (this.totalResults != 0) {
              this.cards = result.data.results;
            }
            this.loading = false;
          })
          .catch((errore) => {
            alert(errore);
          });
      } else { // reset
        this.loading = false;
        this.totalResults = null;
        this.cards= [];
      }
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