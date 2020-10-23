<template lang='html'>
  <body>
    <header>
      <h1>TV show app!!</h1>
    </header>
    <main>
      <tv-show-list v-if='shows.length' :shows='shows'></tv-show-list>
    </main>
    <footer>
      created by Clementine Studios.
    </footer>
  </body>
</template>

<script>
import TvShowList from "./components/TvShowList.vue"

import { eventBus } from '@/main.js';

export default {
  name: 'App',

  data(){
    return{
      shows: [],
      selectedTvShow: null
    }
  },

  mounted(){
    fetch('http://api.tvmaze.com/shows')
    .then(response => response.json())
    .then(data => this.shows = data);

    eventBus.$on('selected-tv-show', (show) => {
      this.selectedTvShow = show
    })
  },

  components: {
    TvShowList,
  }
    
}
</script>

<style lang='css' scoped>

</style>