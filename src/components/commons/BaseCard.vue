<template>     
    <div class="card">
        <img v-if="info.poster_path" class= "img_path" :src="`https://image.tmdb.org/t/p/w185/${info.poster_path}`">
        <img v-else src="https://via.placeholder.com/200x300">
        <h3>{{info.title ? info.title : info.name}}</h3>
        <div class="overlay">
            <h4>{{info.original_title ? info.original_title : info.original_name }}</h4>
            <span v-html="getStars(info.vote_average)"></span>
            <img class="img_flag" :src="getFlag(info.original_language)">
        </div>
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
.card {
    position: relative;
    border: 0.0625rem solid whitesmoke;
}

h3 {
    text-align: center;
    margin: 0.3125rem;
}

h4, span {
    margin: 0.3125rem;
}


.overlay {
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
    height: 100%;
    width: 100%;
    display: none; 
}

.card:hover .overlay {
    display: block;
    background-color: #000000;
    color: #f0f8ff;
}

.card:hover {
    opacity: 0.8;
} 

.img_flag {
    height: 0.625rem;
    width: 0.9375rem;
    margin-left: 0.3125rem;
}

.img_path {
    height: 300px;
    width: 200px;
}
</style>