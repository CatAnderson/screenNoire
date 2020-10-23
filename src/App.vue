<template>
<main>
  <h1>New TV show app!!</h1>
  <ul 
  <li v-for='(show, index) in shows' :key='index' :value='index'> {{ show.name }} </li>

  </ul>
</main>
</template>

<script>
export default {
  name: 'App',

  data(){
    return{
      shows: [],
      selectedShow: null
    }
  },

  mounted(){
    fetch('http://api.tvmaze.com/shows')
    .then(response => response.json())
    .then(data => this.shows = data);
  }
}
</script>

<style>

</style>