<template>
  <form class="searchbar" @submit.prevent="submitForm()">
        <input type="text" placeholder="Search.." name="search" v-model="search">
        <button type="submit"><i class="fa fa-search"></i></button>
    </form>
</template>

<script>
import axios from 'axios';

export default {
    name:'SearchBar',
        data() {
            return {
                search:'',
            }
        },

        methods: {
            // film
        submitForm() {
            axios.get('https://api.themoviedb.org/3/search/movie', {
                params: {
                    api_key:'2fcc653be32b6847d9dbdbc388549bfc',
                    query:this.search,
                    language:'it-IT',
                }
            }).then((response) => {
                console.log(response.data.results);
            }).catch((error) => {
                console.log(error);
            })

            // serir tv
            axios.get('https://api.themoviedb.org/3/search/tv', {
                params: {
                    api_key:'2fcc653be32b6847d9dbdbc388549bfc',
                    query:this.search,
                    language:'it-IT',
                }
            }).then((response) => {
                console.log(response.data.results);
            }).catch((error) => {
                console.log(error);
            })
        },

        
    }
}
</script>

<style>

</style>