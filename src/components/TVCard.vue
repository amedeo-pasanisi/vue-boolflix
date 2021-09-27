<template>
    <li id="movieCard">
        <h3>{{TVCard.name}}</h3>
        <div>{{TVCard.original_name}}</div>
        <div>{{TVCard.original_language}}</div>
        <div>{{TVCard.vote_average}}</div>
    </li>
</template>

<script>
export default {
    name: "MovieCard",
    props: {
        TVCard: Object
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