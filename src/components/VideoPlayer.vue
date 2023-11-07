<script lang="ts">
import videojs from 'video.js'
import 'video.js/dist/video-js.css'
import { defineComponent, ref, onMounted } from 'vue'

type PlayerPropsType = {
  id: string
  mediaType?: string
  src: string
  title: string
  token?: string
  createdAt: string
}

export default defineComponent({
  name: 'VideojsPlayer',
  props: {
    options: {
      type: Object as () => PlayerPropsType,
      default: () => ({}),
      required: true,
    },
  },
  setup(props) {
    const isPlaying = ref<boolean>(false)
    const isSupported = ref<boolean>(false)
    let VideoJSPlayerInstance = null as unknown
    onMounted(() => {
      VideoJSPlayerInstance = videojs(
        'player-element',
        props.options,
        function onPlayerReady() {
          console.log('Player Is: ', VideoJSPlayerInstance)
          console.log(props.options)
        },
      )
    })
  },
})
</script>

<template>
  <div class="container row">
    <br />
    <div class="column">
      <video
        ref="mediacontainer"
        id="player-element"
        class="video-js vjs-default-skin"
        controls
        preload="auto"
      >
        <source
          src="http://commondatastorage.googleapis.com/gtv-videos-bucket/sample/BigBuckBunny.mp4"
        />

        <!-- :type="options.mediaType" -->
    </video>
    </div>
  </div>
</template>
