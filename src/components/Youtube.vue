<template>
  <div class="Youtube">
    <YouTube
      src="97BCBEWDjgc"
      @ready="onReady"
      @stateChange="stateChange"
      ref="youtube"
      :vars="options"
    />
  </div>
</template>

<script>
import YouTube from 'vue3-youtube'
export default {
  data() {
    return {
      videoId: '_ihQJc3A_ig',
      interval: null,
      options: {
        "autoplay": 0,
        "controls": 1,
        "modestbranding": 1,
      },
      first_time: 0,
      last_time: 0,
      durations: 0,
    }
  },
  components: {
    YouTube,
  },
  methods: {
    onReady() {
      console.log("onReady");
      this.$refs.youtube.mute()
    },
    stateChange(a) {
      console.log("stateChange");

      if (this.$refs.youtube.getPlayerState() == 1) {
        this.first_time = a.target.getCurrentTime()
        this.interval = setInterval(() => {
          this.last_time = a.target.getCurrentTime();
          this.durations = Math.round(this.last_time - this.first_time)
          console.log(this.durations);
        }, 1000)
      } else {
        this.first_time = 0
        this.durations = 0
        clearInterval(this.interval)
      }
    }
  },
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
