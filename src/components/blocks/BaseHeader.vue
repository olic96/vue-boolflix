<template>
  <header>
    <div class="logo">
      BOOLFLIX
    </div>
    <SearchBar/>
  </header>
</template>

<script>
import SearchBar from '../sections/SearchBar.vue'

export default {
  components: { SearchBar },
    name:'BaseHeader',
}

</script>

<style>
header {
  display: flex;
  justify-content: space-between;
  background-color: #000000;
}
.logo {
  color: #ff0000;
  font-size: 1.875rem;
  margin: 1.875rem 1.875rem;
}
</style>