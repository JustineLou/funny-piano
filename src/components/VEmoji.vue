<template>
  <div class="emoji-container">
    <img alt="Gif aléatoire" id="EmojiGIF" :src="src" v-if="src"/>
  </div>
</template>

<script>
import { GiphyFetch } from "@giphy/js-fetch-api";
export default {
  GiphyFetch,
  data(){
    return {
      src: null
    }
  },
    methods: {
      //Générer et faire apparaitre un emoji dans l'image
      async generateEmoji(){
      const gf = new GiphyFetch("hoc7Xw81iwUP2iewXhekupQznVmYDlHK");
      const { data: gifs } = await gf.emoji();
      console.log(gifs);
      const gifIndex = Math.floor(Math.random() * 20);
      const gif = gifs[gifIndex].images.downsized.url;
      this.src = gif;
    }, 
    //Retirer l'emoji
    stopEmoji(){
      this.src = null;
    }   
  },
};
</script>



<style lang="postcss"  scoped>
.emoji-container{
    margin-right: auto;
    margin-left: auto;
    width: 200px;
    height: 200px;
    margin-top: 129px;
}


@media only screen and (max-width: 767px) {
    #EmojiGIF {
        margin: auto ;
    }
}

</style>