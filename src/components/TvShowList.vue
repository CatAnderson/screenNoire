<template lang='html'>
<main>
  <div class='scroll-box'>
    <img v-on:click='handleImageClick(show)' v-for='(show, index) in shows' :key='index' :value='index' :src="show.image.medium" alt="tv show poster">
  </div>
  <h2> CHOOSE <br> YOUR <br> SHOW! </h2>
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
        handleImageClick: function(show){
          this.selectedTvShow = show

          eventBus.$emit('selected-tv-show', this.selectedTvShow)
        }
    }

}
</script>

<style lang='css' scoped>


main {
  background-color: #0e0b16;
  display: grid;
  grid-column: span;
  grid-template-columns: 70% 30%;
  margin: 0px;
  padding: 50px;
}

h2 {
  color: #a239ca;
  font-size: 300pt;
  font-weight: 600;
  margin: 0px;
  padding: 0px;
  letter-spacing: 5pt;
  line-height: 250pt;
  align-self: center;
}

img{
  width: 15vw;
  margin: 40px;
  cursor: pointer;
}

.scroll-box{
  width: 70vw;
  height: 40vh;
  overflow: auto;
  white-space: nowrap;
  margin-top: 50px;
  padding: 50px;
}

</style>