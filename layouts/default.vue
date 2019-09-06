<template>
  <v-app>
    <v-navigation-drawer v-model="drawer" app>
      <v-card class="mx-auto" max-width="400" tile>
        <v-list-item v-for="item in items" :key="item.to">
          <v-list-item-content>
            <nuxt-link :to="item.to">
              <v-list-item-title>{{item.title}}</v-list-item-title>
            </nuxt-link>
          </v-list-item-content>
        </v-list-item>
      </v-card>
    </v-navigation-drawer>
    <nuxt-loading />
    <v-app-bar app>
      <v-app-bar-nav-icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
      <nuxt-link :to="{path:'/'}">
        <img :src="require('@/assets/logo.svg')" center height="32" width="32" scale-down />
      </nuxt-link>
      <div class="flex-grow-1"></div>

      <v-btn icon>
        <v-icon>mdi-heart</v-icon>
      </v-btn>

      <v-btn icon>
        <v-icon>mdi-magnify</v-icon>
      </v-btn>
    </v-app-bar>

    <v-content>
      <nuxt />
    </v-content>

    <core-footer app />
  </v-app>
</template>

<script>
import axios from 'axios'
export default {
  name: 'default',
  data() {
    return {
      clipped: false,
      drawer: false,
      fixed: false,
      items: [
        {
          icon: 'mdi-apps',
          title: 'Home',
          to: '/'
        },
        {
          icon: 'mdi-apps',
          title: 'Services',
          to: '/services'
        },
        {
          icon: 'mdi-apps',
          title: 'About',
          to: '/about'
        },
        {
          icon: 'mdi-apps',
          title: 'Contact',
          to: '/contact'
        }
      ],
      miniVariant: false,
      title: 'Mai Test App'
    }
  },
  components: {
    CoreToolbar: () => import('@/components/core/Toolbar'),
    CoreFooter: () => import('@/components/core/Footer'),
    NuxtLoading: () => import('@/.nuxt/components/nuxt-loading')
  },
  methods: {
    openDrawer() {
      this.drawer = drawer == true ? false : true
    }
  }
}
</script>
