<template>
  <div>
    <header-section/>
    <FlightSearch/>

    <!-- <anime-section/> -->
  </div>
</template>

<script>
import FlightSearch from './components/FlightSearch.vue';
import HeaderSection from './components/HeaderSection.vue'

export default {
  name: 'App',
  components: {
    HeaderSection,
    FlightSearch,

  }
}
</script>


<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
