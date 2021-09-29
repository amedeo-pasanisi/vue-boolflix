<template>
    <main id="cards">
        <Loader v-if= "movieLoading || TVLoading" />
        <div v-else-if= "query !=''" class= "container">
            <h4>Movies</h4>
            <h1 v-if= "totalMovieResults == 0">La ricerca non ha prodotto risultati</h1>
            <ul class="movieContainer">
                <Card
                    v-for= "card in movieCards"
                    :key= "card.id"
                    :card= "card"
                />
            </ul>
            <h4>TV series</h4>
            <h1 v-if= "totalTVResults == 0">La ricerca non ha prodotto risultati</h1>
            <ul class="TVContainer">
                <Card
                    v-for= "card in TVCards"
                    :key= "card.id"
                    :card= "card"
                />
            </ul>
        </div>
    </main>
</template>

<script>
import Card from "./Card"
import Loader from "./Loader"
export default {
    name: 'Main',
    components: {
        Card,
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
        h1, h4 {
            text-align: center;
            color: white;
            margin: 10px 0;
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