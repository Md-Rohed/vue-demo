<template>
  <div> 

    <div class="flex justify-between border p-4">
    <div class="font-bold text-xl">Anime</div>
    <div>
      <button @click="searchFlights" class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">Load Anime</button>
    </div>
  </div>
  <div class="grid grid-cols-1 md:grid-cols-3 lg:grid-cols-4 gap-4 p-4">
    <div v-for="anime in searchResults" :key="anime.id" class="bg-white rounded-lg shadow-md overflow-hidden">
      <img :src="'https://shikimori.one' + anime.image.preview" alt="Anime Poster" class="w-full h-64 object-cover">
      <div class="p-4">
        <h2 class="text-xl font-semibold mb-2">{{ anime.name }}</h2>
        <p class="text-gray-700">{{ anime.russian }}</p>
        <p class="text-gray-700">Score: {{ anime.score }}</p>
        <p class="text-gray-700">Episodes: {{ anime.episodes }}</p>
        <p class="text-gray-700">Aired On: {{ anime.aired_on }}</p>
      </div>
    </div>
  </div>
  </div>
  
</template>

<script>
export default {
  name: 'AnimeSection',

  data() {
    return {
      searchResults: []
    };
  },

  methods: {
    async searchFlights() {
      const response = await fetch(`https://shikimori.one/api/animes?page=1&limit=8&order=popularity`, {
        method: 'GET',
        headers: {
          'Content-Type': 'application/json'
        }
      });
      const data = await response.json();
      this.searchResults = data;
      console.log(this.searchResults);
    }
  }
};
</script>

<style scoped>
/* Add your scoped styles here */
</style>
