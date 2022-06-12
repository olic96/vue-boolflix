<template>
  <main>
    <!-- movies -->
    <ul>
      <li v-for="movie in share.movies" :key="movie.id">
        <img class="img_movie" :src="`https://image.tmdb.org/t/p/w185/${movie.poster_path}`">
        <h3>{{movie.title}}</h3>
        <h4>{{movie.original_title}}</h4>
        <span v-html="getStars(movie.vote_average)"></span>
        <img :src="getFlag(movie.original_language)">
      </li>
    </ul>
  <!-- series -->
    <ul>
      <li v-for="serie in share.series" :key="serie.id">
        <img class="img_serie" :src="`https://image.tmdb.org/t/p/w185/${serie.poster_path}`">
        <h3>{{serie.name}}</h3>
        <h4>{{serie.original_title}}</h4>
        <span v-html="getStars(serie.vote_average)"></span>
        <img :src="getFlag(serie.original_language)">
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
        it:'https://i.imgur.com/BA3s6G6.png',
        en:'https://i.imgur.com/QW2YV9c.png',
        es:'https://i.imgur.com/BsLeQa4.png',
        de:'https://i.imgur.com/bhZ7aBe.png',
        fr:'https://i.imgur.com/jwqFDsr.png',
        globe:'https://i.imgur.com/jtA7EG1.jpeg',
      }
    }
  },

  methods: {
    getFlag(original_language) {
      if(original_language === 'en') {
        return this.flag.en;
      } else if(original_language === 'it') {
        return this.flag.it;
      } else if(original_language === 'fr') {
        return this.flag.fr;
      } else if(original_language === 'de') {
        return this.flag.de;
      } else if(original_language === 'es') {
        return this.flag.es;
      } else {
        return this.flag.globe;
      }
    },

    getStars(vote_average) {
      console.log(vote_average)
      let fullstars = '';
      let emptystars = '';
      for (let i = 0; i < Math.ceil(vote_average / 2); i++) {
        fullstars += '<i class="fa-solid fa-star"></i>';
      }
      for (let i = 0; i < (5 - Math.ceil(vote_average / 2)); i++) {
        emptystars += '<i class="fa-regular fa-star"></i>'; 
      }
      return `${fullstars}${emptystars}`;
    }
  }
}
</script>

<style>
  img {
    height: 0.625rem;
    width: 0.9375rem;
  }

  .img_movie {
    height: 300px;
    width: 200px;
  }
</style>