<template lang='html'>
    <article >
        <!-- <h1>this is the tv show details</h1> -->
        <section v-if='show'>
            <hgroup>
            <h3>{{ show.name }}</h3>
            <p>{{ show.summary }}</p>
            <h4>genres:{{ show.genres }}</h4>
            </hgroup>
            <img :src="show.image.original" alt="tv show poster">
        </section>

    </article>
  
</template>

<script>
import { eventBus } from '@/main.js';

export default {
    name: 'tv-show-detail',
    props: ['show'],

    data(){
        return{
        selectedTvShow: null
        }
    },

}
</script>

<style lang='css' scoped>

article{
    display: block;
    border: #a239ca;
    border-style: dotted;
    border-width: 10px;
    margin: 50px;
    justify-items: center;
}

section{
    display: grid;
    grid-template-columns: 50% 50%;
    margin: auto;
}

h3 {
    font-size: 40pt;
    font-weight: 400;
    margin: 0px;
    padding: 20px;
    letter-spacing: 5pt;
}

p {
    font-size: 16pt;
    font-weight: 300;
    margin: 0px;
    padding: 0px 50px;
    /* letter-spacing: 5pt; */
}

img {
    height: 50vh;
    max-width: 100%;
}

</style>