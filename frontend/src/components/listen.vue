<template>
  <section class="page listen">
    <div class="player-btn">
      <span @click="togglePlay">play</span>
    </div>
    <audio class="player" src="../music/a.mp3">
      <p>Your browser does not support the <code>audio</code> element.</p>
    </audio>
    <div class="cd" data-rotation="360" :class="{rotate:isRotate}"></div>
    <div class="lrc">

    </div>
  </section>
</template>
<style>
  .cd{
    background:url('../images/eroman.jpg') top center;
  }
</style>
<script>
  var TWEEN = require('tween');
  export default {
    data(){
          return {
            musicSrc:'music/a.mp3',
            cd:{},
            audio:{},
            isRotate:false,
          }
      },
    mounted(){
      this.audio = document.querySelector('.player');
      this.cd = document.querySelector('.cd');
      new TWEEN.Tween(this.audio.dataset).to({rotation:360},10000).start();
      animate();
      function animate(){
        window.requestAnimationFrame(animate);
        // [...]
        TWEEN.update();
        // [...]
      }

    },
    methods:{

        togglePlay(){
            this.isRotate = !this.isRotate;
            if(this.isRotate){
              this.audio.play();
            }else{
              this.audio.pause();

            }
        }
    }

  }
</script>
