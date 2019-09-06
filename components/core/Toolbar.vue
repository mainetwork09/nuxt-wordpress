<template>
  <div>
    <v-toolbar fixed flat>
      <v-toolbar-side-icon class="hidden-md-and-up" @click="toggleDrawer" />
      <v-container mx-auto py-0>
        <v-layout>
          <v-img
            :src="require('@/assets/logo.png')"
            class="mr-5"
            contain
            height="48"
            width="48"
            max-width="48"
            :to="{path:'/'}"
          />

          <v-spacer />
          <v-text-field
            append-icon="mdi-magnify"
            flat
            hide-details
            solo-inverted
            style="max-width: 300px;"
          />
        </v-layout>
      </v-container>
    </v-toolbar>
  </div>
</template>

<script>
export default {
  data() {
    return {}
  },
  methods: {
    toggleDrawer() {
      return true
    }
  }
}
</script>
