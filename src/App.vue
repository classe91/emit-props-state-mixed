<script>
import axios from 'axios';

import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
import AppSearch from './components/AppSearch.vue';

import { store } from './store'
import { apikey } from '../apikey'

export default {
    components: {
        AppHeader,
        AppMain,
        AppSearch
    },
    data() {
        return {
            store,
        }
    },
    methods: {
        getGames() {

            this.store.loading = true;
            let myUrl = this.store.apiURL;

            if (this.store.categoryValue !== "") {
                myUrl += `?${this.store.apiCategoryParameter}=${this.store.categoryValue}`;
            }

            const config = {
                headers: {
                    'X-RapidAPI-Key': apikey.key,
                    'X-RapidAPI-Host': 'free-to-play-games-database.p.rapidapi.com'
                }
            };

            axios.get(myUrl, config)
                .then((res) => {
                    const maxNumber = res.data.length < this.store.maxResults ? res.data.length : this.store.maxResults;
                    const shortArray = res.data.slice(0, maxNumber);
                    this.store.gamesList = shortArray;
                    this.store.loading = false;
                })
                .catch((err) => {
                    console.log("Error", err);
                });

        },
    },
    created() {
        this.getGames();
    }
};
</script>

<template>
    <AppHeader message="Free Games API" />
    <AppSearch @performSearch="getGames" />
    <AppMain />
</template>


<style lang="scss">
@use './styles/partials/variables' as *;
@use './styles/general.scss';

body {
    background-color: $bg-color;
}

.logo {
    height: 6em;
    padding: 1.5em;
    will-change: filter;
}

.logo:hover {
    filter: drop-shadow(0 0 2em #646cffaa);
}

.logo.vue:hover {
    filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
