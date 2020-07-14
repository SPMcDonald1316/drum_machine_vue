<template>
  <div id="app">
    <b-container>
      <b-row>
        <b-col cols="6" offset="3">
          <b-card class="mt-4">
            <b-row class="justify-content-between mx-2">
              <b-form-checkbox switch size="lg">Power</b-form-checkbox>
              <div class="border px-4 py-2">
                Sound Name
              </div>
            </b-row>
            <b-row class="mx-2 mt-4">
              <label for="volume">Volume</label>
              <b-form-input id="volume" v-model="value" type="range" min="0" max="5"></b-form-input>
            </b-row>
          </b-card>
          <b-card class="my-4">
            <b-row class="justify-content-center">
              <div class="sound-button border" v-for="clip in clips" :key="clip.name">X</div>
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
      clips
    }
  }
}
</script>

<style lang="scss">
  .sound-button {
    width: 160px;
    height: 160px;
  }
</style>
