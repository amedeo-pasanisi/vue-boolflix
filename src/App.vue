<template>
  <div id="app">
    <Header @query= "trigger" />
    <Main
    :query= "query"
    :totalMovieResults= "totalMovieResults"
    :totalTVResults= "totalTVResults"
    :movieCards= "movieCards"
    :TVCards= "TVCards"
    :loading= "loading"
    :movieLoading = "movieLoading"
    :TVLoading = "TVLoading"
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
      apiMovieUrl: "https://api.themoviedb.org/3/search/movie",
      apiTVUrl: "https://api.themoviedb.org/3/search/tv",
      myApyKey: "c8d84c5c4b83aa407def8990d5ce320f",
      lenguage: "it-IT",
      query: "",
      totalMovieResults: null,
      totalTVResults: null,
      movieCards: [],
      TVCards: [],
      loading: false,
      movieLoading: false,
      TVLoading: false
    }
  },
  methods: {
    trigger(query) {
      // ???????????????????????????????
      // const paramsObj = {
      //   params: {
      //     api_key: this.myApyKey,
      //     query: query
      //   }
      // }
      // ???????????????????????????????
      this.query = query;
      this.getApiData();
    },
    getApiData() {
      if (this.query != "") {        
        axios
          .get (this.apiMovieUrl + "?api_key=" + this.myApyKey + "&query=" + this.query + "&language=" + this.lenguage)
          .then ((response) => {
            this.totalMovieResults = response.data.total_results;
            if (this.totalMovieResults != 0) {
              this.movieCards = response.data.results;
            } else {
              this.movieCards = [];
            }
          })
          .catch((errore) => {
            alert(errore);
          });
        axios
          .get (this.apiTVUrl + "?api_key=" + this.myApyKey + "&query=" + this.query + "&language=" + this.lenguage)
          .then ((response) => {
            this.totalTVResults = response.data.total_results;
            if (this.totalTVResults != 0) {
              this.TVCards = response.data.results;
            } else {
              this.TVCards = [];
            }
          })
          .catch((errore) => {
            alert(errore);
          });
      } else { // reset
        this.loading = false;
        this.totalMovieResults = null;
        this.totalTVResults = null;
        this.movieCards= [];
        this.TVCards= [];
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