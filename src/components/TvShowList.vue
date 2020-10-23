<template lang='html'>
<main>
  <h2> pick a show... </h2>
  <img @click='handleClick' id="selected-tv-show" v-for='(show, index) in shows' :key='index' :value='index' :src="show.image.medium" alt="tv show poster">
</main>  
</template>

<script>
import { eventBus } from '@/main.js';

export default {
    name: 'tv-show-list',
    props: ['shows'],

    data(){
        return{
            selectedTvShow: null
        }
    },

    methods:{
        handleClick: function(){
            eventBus.$emit('selected-tv-show', this.selectedTvShow)
        }
    }

}
</script>

<style lang='css' scoped>

</style>