<template>
  <div>
    <img :src="url" alt width="100%" height="300px" />
  </div>
</template>

<script>
export default {
  props: { url: String },
  name: 'hero-cover'
}
</script>

<style lang="scss" scoped>
img {
  object-fit: cover;
}
</style>
