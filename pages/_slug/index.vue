<template>
  <div>
    <hero-cover :url="thumbnail" v-if="loading == false"></hero-cover>
    <v-container v-if="loading == false">
      <v-card class="single-post">
        <v-card-title>
          <h1>{{ title }}</h1>
        </v-card-title>
        <v-card-text v-html="content"></v-card-text>
      </v-card>
    </v-container>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  data() {
    return {
      title: '',
      thumbnail: '',
      content: '',
      loading: true
    }
  },
  components: {
    HeroCover: () => import('@/components/HeroCover')
  },
  mounted() {
    this.$nextTick(() => {
      this.$nuxt.$loading.start()
      axios
        .get('/api/wp/v2/posts?slug=' + this.$route.path)
        .then(res => {
          //console.log(res)
          this.title = res.data[0].title.rendered
          this.thumbnail = res.data[0].jetpack_featured_media_url
          this.content = res.data[0].content.rendered
          this.loading = false
          this.$nuxt.$loading.finish()
        })
        .catch(() => {
          console.error(`Can not load resources`)
        })
    })
  }
}
</script>

<style lang="scss" scoped>
.single-post {
  margin-top: -60px;
  padding: 30px;

  h1 {
    margin-bottom: 20px;
    line-height: 1.5;
  }
}
</style>
