<template>
    <div id="card">
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
        border: 2px solid #1E2D3B;
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