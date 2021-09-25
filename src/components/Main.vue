<template>
    <main id="cards">
        <div class="container">
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
export default {
    name: 'Main',
    components: {
        Card
    },
    props: {
        cards: Array
    },
    data() {
        return {
        }
    },
    // computed: {
    //     filteredDischi () {
    //         if (this.filter == "") {
    //             return this.dischi
    //         }
    //         return this.dischi.filter(
    //             (disco) => disco.genre == this.filter
    //         );
    //     }
    // },
    methods: {
    }
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
        }
    }
</style>