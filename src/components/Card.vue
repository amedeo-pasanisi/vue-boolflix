<template>
    <li id="card">
        <div class="front">
            <img v-if="card.poster_path" :src="`https://image.tmdb.org/t/p/w342${card.poster_path}`">
            <img v-else src="http://lexingtonvenue.com/media/poster-placeholder.jpg" alt="">
        </div>
        <div class="back">
            <h3>{{ card.title ? card.title : card.name }}</h3>
            <p>{{card.original_name ? card.original_name : card.original_title}}</p>
            <img v-if="lenguages.includes(card.original_language)" class="flag" :src="require(`../assets/${card.original_language}.png`)" alt="">
            <p v-else>{{card.original_language}}</p>
            <div>
                <i v-for="n in 5" :key="n"
                    class="fa-star"
                    :class="(n <= getVote()) ? 'fas' : 'far'"
                >
                </i>
            </div>
            <h4>Trama</h4>
            <p>{{card.overview}}</p>
        </div>
    </li>
</template>

<script>
export default {
    name: "Card",
    data() {
        return {
            lenguages: ["en", "it"]
        }
    },
    props: {
        card: Object
    },
    methods: {
        getVote() {
            return Math.ceil(this.card.vote_average / 2);
        }
    }
}
</script>

<style scoped lang="scss">
    #card {
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
        .front {
            img {
                width: 100%;
            }
        }
        .back {
            &>* {
            margin-bottom: 20px;
            }
            .flag {
                width: 40px;
            }
        }
    }
</style>