<template>
    <li id="movieCard">
        <h3>{{movieCard.title}}</h3>
        <div>{{movieCard.original_title}}</div>
        <div>{{movieCard.original_language}}</div>
        <div>{{movieCard.vote_average}}</div>
    </li>
</template>

<script>
export default {
    name: "MovieCard",
    props: {
        movieCard: Object
    }
}
</script>

<style scoped lang="scss">
    #movieCard {
        display: flex;
        flex-direction: column;
        align-items: center;
        text-align: center;
        width: calc(100% / 5);
        min-height: 200px;
        border: 2px solid #1E2D3B;
        padding: 10px;
        background-color: #424c55;
        color: white;
        &>* {
            margin-bottom: 20px;
        }
    }
</style>