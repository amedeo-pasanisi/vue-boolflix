<template>
    <div id="card">
        <!-- <img :src= "card.poster" alt=""> -->
        <h3>{{card.title}}</h3>
        <div>{{card.original_title}}</div>
        <div>{{card.original_language}}</div>
        <div>{{card.vote_average}}</div>
    </div>
</template>

<script>
export default {
    name: "Card",
    props: {
        card: Object
    }
}
</script>

<style scoped lang="scss">
    #card {
        display: flex;
        flex-direction: column;
        align-items: center;
        text-align: center;
        width: calc(100% / 5 - 20px);
        min-height: 200px;
        margin: 0 10px 20px 10px;
        padding: 10px;
        background-color: #424c55;
        color: white;
        // img {
        //     width: 100%;
        //     margin-bottom: 10px;
        // }
        &>* {
            margin-bottom: 20px;
        }
    }
</style>