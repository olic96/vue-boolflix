<template>
  <main>
    <ul>
      <li v-for="movie in share.movies" :key="movie.id">
        <h3>{{movie.title}}</h3>
        <h4>{{movie.original_title}}</h4>
        <p>{{movie.vote_average}}</p>
        <p>{{getFlag(movie.original_language)}}</p>
      </li>
    </ul>

     <ul>
      <li v-for="serie in share.series" :key="serie.id">
        <h3>{{serie.name}}</h3>
        <h4>{{serie.original_title}}</h4>
        <p>{{serie.vote_average}}</p>
        <p>{{getFlag(serie.original_language)}}</p>
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
      flag: {
        it:'https://it.wikipedia.org/wiki/Bandiera_d%27Italia#/media/File:Flag_of_Italy.svg',
        en:'https://it.wikipedia.org/wiki/Bandiera_del_Regno_Unito#/media/File:Flag_of_the_United_Kingdom_(3-5).svg',
        es:'https://it.wikipedia.org/wiki/Bandiera_della_Spagna#/media/File:Flag_of_Spain.svg',
        de:'https://it.wikipedia.org/wiki/Bandiera_della_Germania#/media/File:Flag_of_Germany.svg',
        fr:'https://it.wikipedia.org/wiki/Bandiera_della_Francia#/media/File:Flag_of_France_(1794–1815,_1830–1974,_2020–present).svg',
        globe:'https://it.wikipedia.org/wiki/Bandiera_della_Terra#/media/File:Earth_Day_Flag.png',
      }
    }
  },

  methods: {
    getFlag(original_language) {
      if(original_language === 'en') {
        return this.data.flag.en;
      }
    }
  }
}
</script>

<style>

</style>