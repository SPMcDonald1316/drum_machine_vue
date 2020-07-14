<template>
  <div id="app">
    <b-container>
      <b-row>
        <b-col cols="6" offset="3">
          <b-card class="mt-4">
            <b-row class="justify-content-between mx-2">
              <b-form-checkbox v-model="isOn" switch size="lg">
                Power
              </b-form-checkbox>
              <b-button variant="outline-info" @click="stop">Stop</b-button>
              <div class="border px-4 py-2">
                {{lastPlayed}}
              </div>
            </b-row>
            <b-row class="mx-2 mt-4">
              <label for="volume">Volume</label>
              <b-form-input id="volume" v-model="volume" type="range" min="0" max="5"></b-form-input>
            </b-row>
          </b-card>
          <b-card class="my-4">
            <b-row class="justify-content-center">
              <div 
              :class="['sound-button border m-1', isOn ? 'border-warning' : 'button-disabled']"
              v-for="clip in clips" 
              :key="clip.name"
              @click="playClip(clip)"
              >
                {{clip.name}}
              </div>
            </b-row>
          </b-card>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
import clips from './clips'

export default {
  name: 'App',
  components: {
  },
  data() {
    return {
      clips,
      volume: 2,
      isOn: true,
      lastPlayed: 'No Sound',
      currentAudio: {}
    }
  },
  methods: {
    playClip({name, url}) {
      if (this.isOn) {
        const a = new Audio(url);
        a.volume = this.volume / 5;
        a.play();
        this.currentAudio = a;
        this.lastPlayed = name;
      }
    },
    stop() {
      this.currentAudio.pause()
    }
  }
}
</script>

<style lang="scss">
  .sound-button {
    width: 160px;
    height: 160px;
    border-radius: 4px;
    display: flex;
    justify-content: center;
    align-items: center;
    &:hover {
      cursor: pointer;
    }
  }
  .button-disabled {
    border-color: gray !important;
    background-color: gray;
    &:hover {
      cursor: not-allowed;
    };
  }
</style>
