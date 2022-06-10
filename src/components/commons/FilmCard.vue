<template>
  <div>
      <ul>
        <li v-for="movie in movies" :key="movie.id">
        <img :src="movie.poster_path" :alt="film.title">
        {{movie.title}}<br>
        {{movie.original_title}}
        </li>
      </ul>
  </div>
</template>

<script>


export default {
    name:'FilmCard',
    props: {
        movies: Array,
        series: Array
    },
}
</script>

<style>

</style>