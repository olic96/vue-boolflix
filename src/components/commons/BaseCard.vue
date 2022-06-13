<template>     
    <div class="card">
        <img class= "img_path" :src="`https://image.tmdb.org/t/p/w185/${info.poster_path}`">
        <h3 v-if="info.title">{{info.title}}</h3>
        <h3 v-else>{{info.name}}</h3>
        <h4>{{info.original_title ? info.original_title : info.original_name }}</h4>
        <span v-html="getStars(info.vote_average)"></span>
        <img class="img_flag" :src="getFlag(info.original_language)">
    </div>
</template>

<script>
export default {
    name:'BaseCard',
    props: {
        info: Object,
    },

     data() {
    return {
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
.img_flag {
    height: 0.625rem;
    width: 0.9375rem;
}

.img_path {
    height: 300px;
    width: 200px;
}
</style>