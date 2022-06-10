<template>
  <form class="searchbar" @submit.prevent="searching()">
        <input type="text" placeholder="Search.." name="search" v-model="search" required>
        <button type="submit"><i class="fa fa-search"></i></button>
    </form>
</template>

<script>
import axios from 'axios';
import share from '../../shared/share';

export default {
    name:'SearchBar',
        data() {
            return {
                share,
                search:'',
            }
        },

        methods: {
            // film
        searching() {
            axios.get('https://api.themoviedb.org/3/search/movie', {
                params: {
                    api_key:'2fcc653be32b6847d9dbdbc388549bfc',
                    query:this.search,
                    language:'it-IT',
                }
            }).then((response) => {
                share.movies = response.data.results;
            }).catch((error) => {
                console.log(error);
            })

            // serie tv
            axios.get('https://api.themoviedb.org/3/search/tv', {
                params: {
                    api_key:'2fcc653be32b6847d9dbdbc388549bfc',
                    query:this.search,
                    language:'it-IT',
                }
            }).then((response) => {
                share.series = response.data.results;
            }).catch((error) => {
                console.log(error);
            })
        },
    }
}
</script>

<style>

</style>