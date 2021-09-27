<template>
    <main id="cards">
        <Loader v-if= "movieLoading || TVLoading" />
        <div v-else-if= "query !=''" class= "container">
            <h4>Movies</h4>
            <ul class="movieContainer">
                <h1 v-if= "totalMovieResults == 0">La ricerca non ha prodotto risultati</h1>
                <MovieCard
                    v-for= "(movieCard,index) in movieCards"
                    :key= "index"
                    :movieCard= "movieCard"
                />
            </ul>
            <h4>TV series</h4>
            <ul class="TVContainer">
                <h1 v-if= "totalTVResults == 0">La ricerca non ha prodotto risultati</h1>
                <TVCard
                    v-for= "(TVCard,index) in TVCards"
                    :key= "index"
                    :TVCard= "TVCard"
                />
            </ul>
        </div>
    </main>
</template>

<script>
import MovieCard from "./MovieCard"
import TVCard from "./TVCard"
import Loader from "./Loader"
export default {
    name: 'Main',
    components: {
        MovieCard,
        TVCard,
        Loader
    },
    props: {
        query: String,
        movieCards: Array,
        TVCards: Array,
        totalMovieResults: Number,
        totalTVResults: Number,
        TVLoading: Boolean,
        movieLoading: Boolean
    }
}
</script>

<style scoped lang="scss">
    #cards {
        min-height: 90%;
        background-color: #1E2D3B;
        padding: 60px 0;
        h1 {
            text-align: center;
            color: white;
        }
        .movieContainer {
            display: flex;
            flex-wrap: wrap;
            margin: 20px 0;
            list-style: none;
        }
        .TVContainer {
            display: flex;
            flex-wrap: wrap;
            margin-top: 20px;
            list-style: none;
        }
    }
</style>