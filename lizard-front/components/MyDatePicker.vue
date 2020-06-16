<template>
  <v-container>
    <v-dialog
      ref="dialog"
      v-model="modal"
      :return-value.sync="date"
      width="290px"
      height="100px"
    >
      <template v-slot:activator="{ on }">
        <v-text-field
          v-model="date"
          :label="label"
          :prepend-icon="icon"
          readonly
          v-on="on"
        ></v-text-field>
      </template>
      <v-date-picker v-model="date" color="primary" @click:date="set">
        <v-spacer></v-spacer>
        <v-btn text color="primary" @click="clear">Clear</v-btn>
      </v-date-picker>
    </v-dialog>
  </v-container>
</template>
<script lang="ts">
import { Vue, Component, Prop, Emit } from 'nuxt-property-decorator'
@Component({
  layout: ''
})
export default class MyDatePicker extends Vue {
  /**
   * props
   */
  @Prop({ type: String, required: false, default: '' }) initialDate!: string
  @Prop({ type: String, required: false, default: 'Date' }) label!: string
  @Prop({ type: String, required: false, default: 'mdi-calendar' })
  icon!: string

  /**
   * data
   */
  private modal: boolean = false
  private date: string = this.initialDate

  @Emit('set')
  public set(): String {
    // https://stackoverflow.com/questions/58158283/vuejs-giving-refs-on-this-refs-a-type-to-remove-typescript-errors
    ;(this.$refs.dialog as any).save(this.date)
    return this.date
  }

  @Emit('set')
  public clear(): String {
    ;(this.$refs.dialog as any).save('')
    return ''
  }
}
</script>
