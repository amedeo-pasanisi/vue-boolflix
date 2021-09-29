<template>
    <li class="flip-card">
        <div class="flip-card-inner">
            <div class="flip-card-front">
                <img v-if="card.poster_path" :src="`https://image.tmdb.org/t/p/w342${card.poster_path}`">
                <img v-else src="http://lexingtonvenue.com/media/poster-placeholder.jpg" alt="">
            </div>
            <div class="flip-card-back">
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
    // .flip-card {
    //     display: flex;
    //     flex-direction: column;
    //     align-items: center;
    //     text-align: center;
    //     width: calc(100% / 5);
    //     min-height: 200px;
    //     border: 2px solid #1E2D3B;
    //     padding: 10px;
    //     background-color: #424c55;
    //     color: white;
    //     .flip-card-front {
    //         img {
    //             width: 100%;
    //         }
    //     }
    //     .flip-card-back {
    //         &>* {
    //         margin-bottom: 20px;
    //         }
    //         .flag {
    //             width: 40px;
    //         }
    //     }
    // }
    .flip-card {
        color: white;
        background-color: transparent;
        width: calc(100% / 5);
        height: 290px;
        perspective: 1000px;
    }
    .flip-card:hover .flip-card-inner {
        transform: rotateY(180deg);
    }
    .flip-card-inner {
        position: relative;
        width: 100%;
        height: 100%;
        text-align: center;
        transition: transform 0.8s;
        transform-style: preserve-3d;
    }
    .flip-card-front, .flip-card-back {
        position: absolute;
        width: 100%;
        height: 100%;
        -webkit-backface-visibility: hidden;
        backface-visibility: hidden;
    }
    .flip-card-front {
        background-color: #bbb;
        color: black;
        overflow: hidden;
        img {
            width: 100%;
        }
    }
    .flip-card-back {
        background-color: #424c55;
        color: white;
        padding: 20px;
        transform: rotateY(180deg);
        overflow: auto;
        &>* {
        margin-bottom: 20px;
        }
        .flag {
            width: 40px;
        }
    }
</style>