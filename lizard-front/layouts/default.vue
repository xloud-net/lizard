<template>
  <v-app dark>
    <v-app-bar dark app>
      <v-toolbar-title v-text="title"></v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn icon fab to="/">
        <v-icon>mdi-home</v-icon>
      </v-btn>
      <v-btn icon fab>
        <v-icon>mdi-magnify</v-icon>
      </v-btn>
      <v-btn icon fab>
        <v-icon>mdi-account</v-icon>
      </v-btn>
      <v-menu transition="slide-y-transition" bottom>
        <template v-slot:activator="{ on }">
          <v-btn icon fab v-on="on">
            <v-icon>mdi-dots-vertical</v-icon>
          </v-btn>
        </template>
        <v-list>
          <v-list-item v-for="(item, i) in items" :key="i" :to="item.to">
            <v-icon>{{ item.icon }}</v-icon>
            <v-spacer />
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item>
        </v-list>
      </v-menu>
    </v-app-bar>
    <v-content>
      <router-view />
    </v-content>
    <v-footer dark app>
      <span>&copy; {{ new Date().getFullYear() }}</span>
    </v-footer>
  </v-app>
</template>

<script lang="ts">
import { Vue, Component } from 'nuxt-property-decorator'

@Component
export default class DefaultLayout extends Vue {
  title: string = 'Lizard'
  items: any[] = [
    {
      icon: 'mdi-apps',
      title: 'Welcome',
      to: '/'
    },
    {
      icon: 'mdi-chart-bubble',
      title: 'Avatars',
      to: '/avatars'
    },
    {
      icon: 'mdi-hexagon',
      title: 'Components',
      to: '/components'
    }
  ]
}
</script>
