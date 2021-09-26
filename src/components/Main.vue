<template>
    <main id="cards">
        <Loader v-if= "loading == true" />
        <h1 v-else-if= "totalResults == 0">La ricerca non ha prodotto risultati</h1>
        <div v-else-if= "query !=''" class= "container">
            <Card
                v-for= "(card,index) in cards"
                :key= "index"
                :card= "card"
            />
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
        cards: Array,
        totalResults: Number,
        query: String,
        loading: Boolean
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
        .container {
            height: 100%;
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
        }
    }
</style>