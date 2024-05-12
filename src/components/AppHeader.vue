<script>

    import axios from 'axios';
    import { store } from "../store";

    export default {
        data() {
            return {
                store,
                btnResult: "",
            }
        },

        methods: {
            getInputName: function() {

                // GET NAME
                let btnInput = document.getElementById("input");
                this.btnResult = btnInput.value;
                this.store.searchQuery = this.btnResult;

                // GENERATE MOVIES ARRAY
                axios.get("https://api.themoviedb.org/3/search/movie", {
                params: {
                api_key: this.store.apiKey,
                query: this.store.searchQuery,
                }
                }).then((resp) => {
                    this.store.moviesArray.length = 0;
                    this.store.moviesArray.push(resp.data.results);
                })

                // GENERATE SERIES ARRAY
                axios.get("https://api.themoviedb.org/3/search/tv", {
                params: {
                api_key: this.store.apiKey,
                query: this.store.searchQuery,
                }
                }).then((resp) => {
                    this.store.seriesArray.length = 0;
                    this.store.seriesArray.push(resp.data.results); 
                })

                // CONSOLE LOGS
                console.log("movies");
                console.log(this.store.moviesArray);
                console.log("series");
                console.log(this.store.seriesArray);
            }
        }
    }

    
</script>

<template>
    <div class="container">

        <!-- TITLE -->
        <h1>BOOLFLIX</h1>

        <!-- SEARCHBAR -->
        <div class="navbar">

            <input type="text" id="input" class="f-size">

            <input type="button" value="Search" class="search-btn f-size" @click="getInputName">

        </div>
    </div>
</template>

<style scoped>

    h1 {
        color: darkred;
        font-size: 4vw;
        padding: 2%;
    }

    .container {
        display: flex;
        justify-content: space-between;
        align-items: center;
        background-color: black;
        width: 100%;
    }

    .navbar {
        display: flex;
        justify-content: space-around;
        height: 100%;
        width: 30%;
    }

    .search-btn {
        padding: 2%;
        background-color: darkred;
        color: white;
    }
</style>