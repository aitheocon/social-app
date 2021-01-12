<template>
<v-container>
    <v-bottom-navigation
    :value="value"
    color="teal"
    grow
  >
    <v-btn>
      <a
            href="../posts"
            target="_blank"
          >POSTS</a>

      <v-icon>mdi-history</v-icon>
    </v-btn>

    <v-btn>
      <a
        href="../myposts"
        target="_blank"
        >MY POSTS</a>

      <v-icon>mdi-heart</v-icon>
    </v-btn>

    <v-btn>
      <a
        href="../profile"
        target="_blank"
        >PROFILE</a>

      <v-icon>mdi-map-marker</v-icon>
    </v-btn>
  </v-bottom-navigation>
  <router-view/>
  </v-container>
</template>

<script>

export default {
  name: 'App',

    data: () => ({ value: 1 }),
 
};
</script>
