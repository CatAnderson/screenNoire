<template lang='html'>
<main>
  <div class='scroll-box'>
    <img @click='handleClick' id="selected-tv-show" v-for='(show, index) in shows' :key='index' :value='index' :src="show.image.medium" alt="tv show poster">
  </div>
  <h2> pick a show... </h2>
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


main {
  
  display: grid;
  grid-template-columns: 80% 20%;
}

h2 {
  font-size: 60pt;
}

.scroll-box{
  width: 80vw;
  height: 40vh;
  overflow: scroll;
}

</style>