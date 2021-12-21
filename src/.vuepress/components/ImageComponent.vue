<template>
  <img :src="$withBase(src)" :style="styles"></iframe>
</template>
<script>

export default {
  props: ['src', 'styles']
}
</script>

