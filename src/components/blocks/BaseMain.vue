<template>
  <main>
    <section>
      <!-- movie -->
      <h2>Films</h2>
      <ul>
        <li v-for="movie in share.movies" :key="movie.id">
          <BaseCard :info="movie"/>
        </li>
      </ul>
    </section>
     <!-- serie -->
    <section>
      <h2>Serie TV</h2>
      <ul>
        <li v-for="serie in share.series" :key="serie.id">
          <BaseCard :info="serie"/>
        </li>
      </ul>
    </section>
  </main> 
</template>

<script>
import share from '../../shared/share';
import BaseCard from '../commons/BaseCard.vue';

export default {
  components: { BaseCard },
  name: 'BaseMain', 

  data() {
    return {
      share,
    }
  },
}
</script>

<style>
main {
  height: 100%;
  background-color: #808080;
  overflow-y: auto;
}

section {
  height: 100vh;
}

h2 {
  margin: 0.625rem;
}

ul {
   display: flex;
}

ul li {
  list-style: none;
  margin: 0.625rem;
}
</style>