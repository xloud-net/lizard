<template>
  <v-card max-width="450" class="mx-auto">
    <v-toolbar color="cyan" dark>
      <v-toolbar-title>Inbox</v-toolbar-title>

      <v-spacer></v-spacer>

      <v-btn icon>
        <v-icon>mdi-magnify</v-icon>
      </v-btn>
    </v-toolbar>

    <v-list three-line>
      <template v-for="(item, index) in items">
        <v-list-item :key="item.title" @click="mainImage = item.avatar">
          <v-list-item-avatar>
            <v-img :src="item.avatar" position="top"></v-img>
          </v-list-item-avatar>

          <v-list-item-content>
            <v-list-item-title>{{ item.name }}</v-list-item-title>
            <v-list-item-subtitle>{{ index + 1 }}</v-list-item-subtitle>
            <v-list-item-subtitle>{{ item.position }}</v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>
      </template>
    </v-list>
    <v-divider></v-divider>
    <v-img :src="mainImage"></v-img>
  </v-card>
</template>
<script lang="ts">
import { Vue, Component } from 'nuxt-property-decorator'

interface Player {
  name: string
  avatar: string
  position: string
}
@Component
export default class Avatars extends Vue {
  /**
   * data
   */
  private mainImage: string = ''
  private imageUrl: string = 'https://joeschmoe.io/api/v1/random'
  private items: Player[] = [
    {
      name: 'Cristiano RONALDO',
      avatar:
        'https://www.juventus.com/media/images/posati/stagione-19-20/prima-squadra/2_501x752_RONALDO.png',
      position: 'Forward'
    },
    {
      name: 'Paulo DYBALA',
      avatar:
        'https://www.juventus.com/media/images/posati/stagione-19-20/prima-squadra/2_501x752_DYBALA.png',
      position: 'Forward'
    },
    {
      name: 'Giorgio CHIELLINI',
      avatar:
        'https://www.juventus.com/media/images/posati/stagione-19-20/prima-squadra/2_501x752_CHIELLINI.png',
      position: 'Defender'
    },
    {
      name: 'Matthijs DE LIGT',
      avatar:
        'https://www.juventus.com/media/images/posati/stagione-19-20/prima-squadra/2_501x752_DELIGT.png',
      position: 'Defender'
    },
    {
      name: 'Leonardo BONUCCI',
      avatar:
        'https://www.juventus.com/media/images/posati/stagione-19-20/prima-squadra/2_501x752_BONUCCI.png',
      position: 'Defender'
    },
    {
      name: 'Gianluigi BUFFON',
      avatar:
        'https://www.juventus.com/media/images/posati/stagione-19-20/prima-squadra/2_501x752_BUFFON.png',
      position: 'GoalKeeper'
    }
  ]
}
</script>
