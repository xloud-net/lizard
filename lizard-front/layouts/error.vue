<template>
  <v-app dark>
    <h1 v-if="error.statusCode === 404">
      {{ pageNotFound }}
    </h1>
    <h1 v-else>
      {{ otherError }}
    </h1>
    <NuxtLink to="/">
      Home page
    </NuxtLink>
  </v-app>
</template>

<script lang="ts">
import { Prop, Vue, Component } from 'nuxt-property-decorator'
@Component
export default class Error extends Vue {
  @Prop({ type: Object, required: true })
  public error: any

  pageNotFound = '404 Not Found'
  otherError = 'An error occurred'

  public static layout = (ctx: any) => {
    if (ctx.app.nuxt.err.statusCode === 404) {
      return 'empty'
    }
    return 'empty'
  }

  public head(): any {
    const title =
      this.error.statusCode === 404 ? this.pageNotFound : this.otherError
    return {
      title
    }
  }
}
</script>

<style scoped>
h1 {
  font-size: 20px;
}
</style>
