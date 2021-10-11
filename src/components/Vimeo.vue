<template>
  <div class="Vimeo">
    <vue-vimeo-player
      ref="vimeo"
      :video-id="videoID"
      :player-height="height"
      @ready="onReady"
      @seeking="seeking"
      @play="play"
      @pause="pause"
      :options="options"
    />
  </div>
</template>

<script>
import { vueVimeoPlayer } from 'vue-vimeo-player'

export default {
  data() {
    return {
      videoID: '491302685',
      height: 500,
      options: {
        muted: false,
        autoplay: true,
      },
      playerReady: false,
      interval: null,
    }
  },
  components: { vueVimeoPlayer },
  methods: {
    onReady() {
      this.playerReady = true
    },
    play(data, player) {
      console.log("onPlay");
      console.log(data, player);
      this.interval = setInterval(() => {
        player.getCurrentTime().then(e =>{console.log(e)})
      }, 1000)
    },
    pause() {
      console.log("onPause");
      clearInterval(this.interval)
    },
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
