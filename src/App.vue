<template lang='html'>
  <body>
    <header>
      <h1>showNoire</h1>
    </header>

    <main>
      <tv-show-list v-if='shows.length' :shows='shows'></tv-show-list>

      <section>
        <div>
          <tv-show-detail v-if="selectedTvShow" :show='selectedTvShow'></tv-show-detail>
          <button v-if='!favouriteTvShows.includes(selectedTvShow)' v-on:click='addToFavourites'>add show</button>
        </div>

      <favourite-tv-shows :favouriteTvShows='favouriteTvShows'></favourite-tv-shows>
      </section>
    </main>

    <footer>
      created by Clementine Studios.
    </footer>
  </body>
</template>

<script>
import TvShowList from "./components/TvShowList.vue"
import TvShowDetail from "./components/TvShowDetail.vue"
import FavouriteTvShowList from "./components/FavouriteTvShowList.vue"

import { eventBus } from '@/main.js';

export default {
  name: 'App',

  data(){
    return{
      shows: [],
      selectedTvShow: null,
      favouriteTvShows: []
    }
  },

  mounted(){
    fetch('http://api.tvmaze.com/shows')
      .then(response => response.json())
      .then(data => this.shows = data);

    eventBus.$on('selected-tv-show', (show) => {
      this.selectedTvShow = show
    })

    eventBus.$on('selected-favourite-tv-show', (favouriteTvShow) => {
      this.favouriteTvShows.splice(this.favouriteTvShows.indexOf(favouriteTvShow), 1)
    })
  },

  methods: {
    addToFavourites: function(){
      this.favouriteTvShows.push(this.selectedTvShow)
    }
  },

  components: {
    'tv-show-list': TvShowList,
    'tv-show-detail': TvShowDetail,
    'favourite-tv-shows': FavouriteTvShowList
  }
    
}
</script>

<style lang='css' scoped>
@import url("https://fonts.googleapis.com/css2?family=Kanit:wght@300;400;600;800&display=swap");

body{
  font-family: 'Kanit', sans-serif;
  justify-content: center;
  text-align: center;
  margin: 0px;
  width: 100vw;
  height: 100vh; 
  background-color: #0e0b16;
  color: #e7dfdd;
}

header {
  background-image: linear-gradient(to right, #a239ca, #4717f6 );
  color: #e7dfdd;
  padding-bottom: 50px;
  padding-top: 50px;
}

h1 {
  font-size: 80pt;
  font-weight: 300;
  letter-spacing: 8pt;
  border: #e7dfdd;
  border-style: dotted;
  border-width: 10px;
  margin: 0px 300px;
}

section {
  display: grid;
  grid-template-columns: 50% 50%;
  background-color: #0e0b16;
}

button{
    display: block;
    background-color: #4717f6;
    color: #e7dfdd;

    width: 200px;
    height: 10px;

    padding: 20px;
    border-radius: 10px;
    margin: auto;
    margin-bottom: 50px;

    text-decoration: none;
    text-align: center;
    line-height: 2px;

    font-size: 20pt;
    font-weight: 800;
}

footer{
  background-image: linear-gradient(to right, #a239ca, #4717f6 );
  color: #e7dfdd;
  padding: 30px;
}
</style>