<template lang='html'>
    <article >
        <!-- <h1>this is the tv show details</h1> -->
        <section v-if='show'>
            <hgroup>
            <h3>{{ show.name.toUpperCase() }}</h3>
            <p>{{ show.summary.replace(/(<([^>]+)>)/gi,"") }}</p>
            <h4>GENRE: <br> {{ show.genres.join(`, &nbsp;`).toString() }}</h4>
            <h4>SHOW RATING: <br> {{ show.rating.average }}</h4>
            <h4>STATUS: <br> {{ show.status }}</h4>
            <!-- <button v-if='!favouriteTvShows.includes(selectedTvShow)' v-on:click='addToFavourites'>add show</button> -->
            </hgroup>
            <img :src="show.image.original" alt="tv show poster">
        </section>

    </article>
  
</template>

<script>
// import { eventBus } from '@/main.js';

export default {
    name: 'tv-show-detail',
    props: ['show'],

    data(){
        return{
        selectedTvShow: null,
        favouriteTvShows: []
        }
    },
    // methods: {
    //     addToFavourites: function(){
    //         this.favouriteTvShows.push(this.selectedTvShow)
    //     }
    // },

}
</script>

<style lang='css' scoped>

article{
    display: block;
    border: #a239ca;
    border-style: dotted;
    border-width: 8px;
    margin: 40px;
    justify-items: center;
}

section{
    display: grid;
    grid-template-columns: 50% 50%;
    margin: auto;
}

h3 {
    font-size: 30pt;
    font-weight: 400;
    margin: 0px;
    padding: 20px;
    letter-spacing: 5pt;
}

p {
    font-size: 10pt;
    font-weight: 300;
    margin: 0px;
    padding: 0px 40px;
    /* letter-spacing: 5pt; */
}

h4 {
    font-size: 14pt;
    font-weight: 600;
    color: #a239ca;
    letter-spacing: 2pt;
}
hgroup{
    align-self: center;
}

img {
    height: 70vh;
    max-width: 100%;
    justify-content:right;
}

</style>