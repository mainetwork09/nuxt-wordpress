<template>
  <div>
    <v-container>
      <div class="row">
        <div class="col-lg-4" v-for="item in posts" :key="item.ID">
          <v-card>
            <v-img>
              <img :src="item.jetpack_featured_media_url" width="100%" alt />
            </v-img>
            <v-card-title>{{ item.title.rendered }}</v-card-title>
            <v-card-actions>
              <v-btn block text color="primary" :to="{path:item.slug}">Read More</v-btn>
            </v-card-actions>
          </v-card>
        </div>
      </div>
    </v-container>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  data() {
    return {
      title: 'test',
      posts: [],
      loading: true
    }
  },
  mounted: function() {
    this.$nextTick(() => {
      this.$nuxt.$loading.start()
      axios
        .get('/api/wp/v2/posts')
        .then(res => {
          this.posts = res.data
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

<style lang="scss">
.v-image {
  img {
    height: 200px;
    object-fit: cover;
  }
}
</style>
