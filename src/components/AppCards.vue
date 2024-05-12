<script>

    import axios from 'axios';
    import { store } from '../store';

    export default {

        data() {
            return {
                store,
            }
        },
        
        methods: {
            reciveEmit() {
                console.log("ciao");
            }
        }
    }

</script>

<template>
    <div class="container">

        <!-- MOVIES CARD -->
        <div class="card" v-for="(moviesCard, index) in this.store.moviesArray[0]">

            <!-- FRONT -->
            <div class="card-img">

                <img :src="`https://image.tmdb.org/t/p/w500/${this.store.moviesArray[0][index].poster_path}`" :alt="this.store.moviesArray[0][index].title">

            </div>

            <!-- BACK -->
            <div class="card-back f-size">

                <!-- INFO -->
                <div>

                    <div><b>Title:</b> {{ this.store.moviesArray[0][index].title }}</div>
                    <div><b>Original Title:</b> {{ this.store.moviesArray[0][index].original_title }}</div>
                    <div><b>Vote:</b> {{ this.store.moviesArray[0][index].vote_average }}</div>
                    <div><b>Overview:</b> {{ this.store.moviesArray[0][index].overview }}</div>

                </div>
                
                <!-- LANGUAGE -->
                <div><b>Language:</b> {{ this.store.moviesArray[0][index].original_language }}</div>

            </div>

        </div>


        <!-- SERIES CARD -->
        <div class="card" v-for="(seriesCard, index) in this.store.seriesArray[0]">

            <!-- FRONT -->
            <div class="card-img">

                <img :src="`https://image.tmdb.org/t/p/w500/${this.store.seriesArray[0][index].poster_path}`" :alt="this.store.moviesArray[0][index].title">

            </div>

            <!-- BACK -->
            <div class="card-back f-size">

                <!-- INFO -->
                <div>

                    <div><b>Title:</b> {{ this.store.seriesArray[0][index].name }}</div>
                    <div><b>Original Title:</b> {{ this.store.seriesArray[0][index].original_name }}</div>
                    <div><b>Vote:</b> {{ this.store.seriesArray[0][index].vote_average }}</div>
                    <div><b>Overview:</b> {{ this.store.seriesArray[0][index].overview }}</div>

                </div>
                
                <!-- LANGUAGE -->
                <div><b>Language:</b> {{ this.store.seriesArray[0][index].original_language }}</div>

            </div>

        </div>

    </div>
</template>

<style scoped>

    .container {
        display: flex;
        flex-wrap: wrap;
        padding: 5%;
        background-color: gray;
        width: 100%;
    }

    .card {
        padding: 2%;
        width: 33%;
    }

    .card-img {
        width: 100%;
        height: 100%;
    }

    .card:hover .card-img {
        display: none;
    }
    
    .card:hover .card-back {
        display: flex;
    }

    .card-back {
        display: none;
        flex-direction: column;
        justify-content: space-between;
        height: 100%;
        width: 100%;
        padding: 5% 3%;
        background-color: black;
        color: lightgray;

        b {
            font-size: 1.7vw;
            color: white;
        }

        div {
            padding: 1% 1%;
        }
    }

</style>
