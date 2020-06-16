<template>
  <v-layout column justify-center align-center>
    <PostPreview :post="post"></PostPreview>
    <MyDatePicker
      label="Birthday"
      :initial-date="birthday"
      @set="setBirthday"
    ></MyDatePicker>
    <p>Birthday is {{ birthday }}</p>
    <v-divider />
    <MyDatePicker
      label="Today"
      :initial-date="today"
      @set="setToday"
    ></MyDatePicker>
    <p>Today is {{ today }}</p>
  </v-layout>
</template>

<script lang="ts">
/**
 * about 'nuxt-property-decorator'
 * https://qiita.com/simochee/items/e5b77af4aa36bd0f32e5
 * https://shigekitakeguchi.github.io/2019/10/11/1.html
 */
import { Component, Vue } from 'nuxt-property-decorator'
import moment from 'moment'
import MyDatePicker from '@/components/MyDatePicker.vue'

@Component({
  components: {
    MyDatePicker,
    PostPreview: () => import('~/components/PostPreview.vue')
  }
})
export default class Components extends Vue {
  /**
   * data
   */
  private birthday: string = ''
  private today: string = moment().format('YYYY-MM-DD')
  private post: object = {
    title: 'This is Title',
    description: 'This is Description'
  }

  /**
   * methods
   */
  public setBirthday(birthday: string): void {
    this.birthday = birthday
  }

  public setToday(today: string): void {
    this.today = today
  }
}
</script>
