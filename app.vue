<script setup lang="ts">
import { ref, onMounted } from 'vue';
import videojs, { VideoJsPlayer } from 'video.js'
// import { WowzaWebRTCPlayer } from 'wowza-webrtc-player';



const videoPlayer = ref();
var player: VideoJsPlayer;

onMounted(async () => {
  if (process.client) {
    let wowza = await import("wowza-webrtc-player");
    const player = new wowza.WowzaWebRTCPlayer(videoPlayer.value, {
      sdpUrl: 'wss://639fdc2445489.streamlock.net:1955/webrtc-session.json',
      applicationName: 'testLive',
      streamName: 'rtck',
    });

    await player.playRemote();
    console.log(player)
  }

});

</script>
<template>

  <Head>
    <Link rel="stylesheet" href="https://unpkg.com/video.js/dist/video-js.css" />
  </Head>
  <div>
    <div>
      <video ref="videoPlayer" autoplay muted style="width: 100vw; height: 56.25vw"></video>
    </div>
  </div>
</template>
