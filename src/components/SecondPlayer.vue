<template>
  <div>
    <base-player :options="videoOptions" />
  </div>
</template>

<script>
import BasePlayer from '@/components/BasePlayer.vue'

export default {
  name: 'VideoJSExample',
  components: {
    BasePlayer
  },
  data() {
    return {
      videoOptions: {
        autoplay: true,
        controls: true,
        preload: true,
        fluid: true,
        sources: [
          {
            src: 'http://commondatastorage.googleapis.com/gtv-videos-bucket/sample/BigBuckBunny.mp4',
            type: 'video/mp4'
          }
        ]
      }
    }
  }
}
</script>
