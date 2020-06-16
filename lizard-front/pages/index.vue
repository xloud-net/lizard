<template>
  <v-layout column justify-center align-center>
    <v-flex xs12 sm8 md6>
      <v-card>
        <v-card-title class="headline">
          {{ messageEdited }}
        </v-card-title>
        <v-card-actions>
          <v-spacer />
          <v-btn color="primary" @click="changeMessage">
            Change
          </v-btn>
          <v-btn color="primary" nuxt to="/components">
            Continue
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-flex>
  </v-layout>
</template>

<script lang="ts">
/**
 * about 'nuxt-property-decorator'
 * https://qiita.com/simochee/items/e5b77af4aa36bd0f32e5
 * https://shigekitakeguchi.github.io/2019/10/11/1.html
 */
import { Component, Vue } from 'nuxt-property-decorator'

@Component
export default class Index extends Vue {
  /**
   * data
   */
  private message: string = ''

  /**
   * computed
   */
  private get messageEdited(): string {
    return this.message + 'World!'
  }

  /**
   * mounted
   */
  private mounted() {
    this.message = 'Hello'
  }

  /**
   * beforeDestroy
   */
  private beforeDestroy() {
    this.message = ''
  }

  /**
   * methods
   */
  private changeMessage(): void {
    this.message = 'Change The '
  }
}
</script>
