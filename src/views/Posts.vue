<template>
  <div class="posts">
    <PostTable msg="Welcome to the Post page"/>
  </div>
</template>

<script>

import PostTable from '@/components/PostTable.vue'

export default {
  name: 'Posts',
  components: {
    PostTable
  }
}
</script>