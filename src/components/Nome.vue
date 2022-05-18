<template>
    <button v-on:click="start">start</button>
    <button v-on:click="stop">stop</button>
    <p>{{ message }}</p>
    bpm: <input v-model="bpm" />
    meter: <input v-model="pai" />
    <audio ref="marker_audio_1" :src="audio_1_src"/>
    <audio ref="marker_audio_2" :src="audio_2_src"/>

</template>

<script>

export default {
  name: 'Nome',
  data() {
    return {
        bpm: 120,
        pai: 4,
        audio_1_src: require("../assets/marker_sound.mp3"),
        audio_2_src: require("../assets/marker_sound_2.mp3"),
        audio_1_loop: null,
        audio_2_loop: null,
        count: 0
    }
  },
  computed: {
    interval_period() {
        return 60 / this.bpm;
    }
  },    
  methods : {
      start() {
        this.stop();
        this.count = 0;
        console.log(this.interval_period);
        this.audio_1_loop = setInterval(this.play_marker, this.interval_period * 1000);
      },
      stop() {
        if (this.audio_1_loop) {
            clearInterval(this.audio_1_loop);
        }
        if (this.audio_2_loop) {
            clearInterval(this.audio_2_loop);
        }
        this.count = 0;
      },
      play_marker() {
        if (this.count % this.pai == 0) {
            this.$refs.marker_audio_1.play();
        } else {
            this.$refs.marker_audio_2.play();
        }
        this.count++;
      }
  }
}
</script>

<style>
</style>
