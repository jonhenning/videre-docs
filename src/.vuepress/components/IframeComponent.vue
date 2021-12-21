<template>
  <div class="video-container">
    <iframe allowfullscreen="" frameborder="0" :src="src"></iframe></div>
  </div>
</template>
<style scoped>
.video-container {
    margin-top: 10px;
    position: relative;
    padding-bottom: 56.25%;
    padding-top: 30px; height: 0; overflow: hidden;
}
 
.video-container iframe,
.video-container object,
.video-container embed {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
}
</style>

<script>

export default {
  props: ['src']
}
</script>

