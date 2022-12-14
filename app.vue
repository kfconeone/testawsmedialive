<template>
  <div>
    <video-js ref="videoPlayer" class="video-js" controls>
      <source :src="hlsUrl" type="application/x-mpegURL" />
    </video-js>
  </div>
</template>

<script>
import videojs from 'video.js'

export default {
  data() {
    return {
      hlsUrl: "https://cx7nx2tbdgudme.data.mediastore.us-east-1.amazonaws.com/livea/main.m3u8"
    }
  },
  mounted() {
    this.player = videojs(this.$refs.videoPlayer, {
      // options
    })
  }
}
</script>