<template>
    <div>
       <video ref="VideoJsPlayer" id="video-player" class="video-js vjs-defaultskin" controls>
        <!-- <source
          src="http://commondatastorage.googleapis.com/gtv-videos-bucket/sample/BigBuckBunny.mp4"
        /> -->
       </video>
    </div>
 </template>
 <script lang="ts">
    import videojs from 'video.js';
    let VideoJSPlayerInstance = null as unknown

    export default {
       name: 'BasePlayer',
       props: {
          options: {
             type: Object,
             default() {
                return {};
             }
          }
       },
       data() {
          return {
          player: null
       }
    },
    mounted() {
        VideoJSPlayerInstance = videojs('video-player', 
        this.options, 
        function onPlayerReady () {
            console.log('Player Is: ', VideoJSPlayerInstance)
       });
    },
 }
 </script>