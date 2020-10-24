<template lang='html'>
    <aside>
        <h1>YOUR FAVOURITE TV SHOWS!</h1> 
        <ul>
            <li v-for='favouriteTvShow in favouriteTvShows' :key='index' v-model="selectedFavouriteTvShow"> <img :src="favouriteTvShow.image.medium" alt="tv show poster">
            <br>
            <button v-on:click="updateTvShow(favouriteTvShow)">remove</button>
            </li>
        </ul>
    </aside>
  

</template>

<script>
import { eventBus } from '@/main.js';

export default {
    name: 'favourite-tv-shows',
    props: ['favouriteTvShows'],

    data(){
        return {
            selectedFavouriteTvShow: null
        }
    },

    methods: {
        updateTvShow: function(favouriteTvShow) {
            this.selectedFavouriteTvShow = favouriteTvShow;

            eventBus.$emit('selected-favourite-tv-show', this.selectedFavouriteTvShow)
        }
    }
}
</script>

<style lang='css' scoped>

aside{
    display: block;
    border: #a239ca;
    border-style: dotted;
    border-width: 10px;
    margin: 50px;
}

h1{
    font-size: 40pt;
    font-weight: 400;
    margin: 0px;
    padding: 20px;
    letter-spacing: 5pt;
}
ul {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    margin: auto;
    padding: 0px 40px 40px 40px;
}
li {
    list-style-type: none;
}

li > img{
    height: 20vh;
    padding: 10px;
    padding-top: 50px;
    /* margin: 20px; */
}

button {
    display: block;
    background-color: #a239ca;
    color: #e7dfdd;

    width: 200px;
    height: 10px;

    padding: 20px;
    border-radius: 10px;
    margin: auto;

    text-decoration: none;
    text-align: center;
    /* vertical-align: middle; */
    line-height: 2px;

    font-size: 20pt;
    font-weight: 800;
}

</style>