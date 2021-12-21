<template>
  <img :src="$withBase(src)" :style="style"></iframe>
</template>
<script>

export default {
  props: ['src', 'style']
}
</script>

