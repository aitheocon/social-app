<template>
  <div class="posts">
    <PostTable msg="Welcome to the My Posts page"/>
  </div>
</template>

<script>

import PostTable from '@/components/PostTable.vue'

export default {

  components: {
    PostTable
  }
}
</script>