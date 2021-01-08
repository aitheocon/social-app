<template>
  <v-app>
    <v-main>
    <nav class="navbar navbar-expand-sm bg-dark navbar-dark">
      <ul class="navbar-nav">
        <li class="nav-item">
          <router-link to="/" class="nav-link">Home</router-link>
        </li>
        <li class="nav-item">
          <router-link to="/posts" class="nav-link">Posts</router-link>
        </li>
        <li class="nav-item">
          <router-link to="/myposts" class="nav-link">My Posts</router-link>
        </li>
        <li class="nav-item">
          <router-link to="/profile" class="nav-link">Profile</router-link>
        </li>
      </ul>
    </nav> 
    </v-main>
    <router-view/>
  </v-app>
</template>

<script>

export default {
  name: 'App',

 

  data: () => ({
    //
  }),
};
</script>
