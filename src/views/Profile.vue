<template>
  <div class="posts">
    <ProfilePage msg = "This is the profile page"/>
  </div>
</template>

<script>

import ProfilePage from '@/components/ProfilePage.vue'

export default {
  name: 'Profile',
  components: {
    ProfilePage
  }
}
</script>