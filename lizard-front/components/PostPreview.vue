<template>
  <div>
    <hr />
    <h2>{{ post.title }}</h2>
    <p>{{ post.description }}</p>
    <hr />
  </div>
</template>

<script lang="ts">
import { Vue, Component, Prop } from 'nuxt-property-decorator'

interface Post {
  title: string
  description: string
}

@Component
export default class PostPreview extends Vue {
  @Prop({ type: Object, required: true }) post!: Post
}
</script>
