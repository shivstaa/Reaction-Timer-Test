<template>
    <p>Reaction time - {{ score }} ms</p>
    <p class="rank">{{ rank }}</p>
    <video v-if="videoSource" width="320" height="240" controls>
      <source :src="videoSource" type="video/mp4">
    </video>
    <br>
  </template> 
  
  <script>
  import TerribleVideo from '../assets/terrible.mp4'
  import FastVideo from '../assets/fast.mp4'
  import DecentVideo from '../assets/decent.mp4'

  export default {
      props: ['score'],
      data() {
          return {
              rank: null
          }
      },
      computed: {
          videoSource() {
            if (this.score < 300) {return FastVideo}
            else if (this.score < 500) {return DecentVideo} 
            else {return TerribleVideo}
          }
      },
      mounted() {
          if (this.score < 300) {
              this.rank='top notch!'
          }
          else if(this.score < 500) {
              this.rank='pretty quick!'
          }
          else {
              this.rank='terrible...'
          }
      }
  }
  </script>
  
  <style>
  .rank {
    font-size: 1.4em;
    color: #0faf87;
    font-weight: bold;
    color: white;
  }
  </style>
  