<template>
    <main id="cards">
        <div class= "container">
            <h1 v-if= "cards == 'empty'">La ricerca non ha prodotto risultati</h1>
            <Card
                v-else
                v-for= "(card,index) in cards"
                :key= "index"
                :card= "card"
            />
        </div>
    </main>
</template>

<script>
import Card from "./Card"
export default {
    name: 'Main',
    components: {
        Card
    },
    props: ["cards", "query"]
}
</script>

<style scoped lang="scss">
    #cards {
        min-height: 90%;
        background-color: #1E2D3B;
        padding: 60px 0;
        .container {
            width: 90%;
            height: 100%;
            margin: auto;
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            h1 {
                color: white;
            }
        }
    }
</style>