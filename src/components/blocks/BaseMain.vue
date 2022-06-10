<template>
  <main>
    <ul>
      <li v-for="movie in share.movies" :key="movie.id">
        <h3>{{movie.title}}</h3>
        <h4>{{movie.original_title}}</h4>
        <p>{{movie.vote_average}}</p>
      </li>
    </ul>

     <ul>
      <li v-for="serie in share.series" :key="serie.id">
        <h3>{{serie.name}}</h3>
        <h4>{{serie.original_title}}</h4>
        <p>{{serie.vote_average}}</p>
      </li>
    </ul>
  </main> 
</template>

<script>
import share from '../../shared/share';

export default {
  name: 'BaseMain',
  data() {
    return {
      share,
    }
  }
}
</script>

<style>

</style>