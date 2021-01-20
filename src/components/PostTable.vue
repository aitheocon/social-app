<template>
  <div>
  <v-card
    max-width="450"
    class="mx-auto"
  >
    <v-toolbar
      color="cyan"
      dark
    >
      <v-app-bar-nav-icon></v-app-bar-nav-icon>
      <v-toolbar-title>Posts</v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn icon>
        <v-icon>mdi-magnify</v-icon>
      </v-btn>
    </v-toolbar>
    <v-list three-line v-for="post in posts" :key="post._id">
        <v-divider
          v-if= true
          :key="index"
          :inset= true
        ></v-divider>

        <v-list-item
          v-else
          :key="post.title"
        >
        
          <v-list-item-content>
            <v-list-item-title v-html="post.title"></v-list-item-title>
            <v-list-item-subtitle> {{ post.body }} </v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>
    </v-list>
  </v-card>
  <form @submit.prevent="addPost">
    <v-text-field
      label="Title"
      :rules="rules"
      hide-details="auto"
      v-model="p.title"
    ></v-text-field>
    <v-text-field label="Message" v-model="p.body"></v-text-field>
    <v-btn
    class="form-group"
    elevation="2"
    fab
    >
    <v-icon>mdi-plus</v-icon>
    </v-btn>
    </form>
  </div>
</template>

<script>
  export default {
      name: 'PostTable',

    data: () => ({
      posts: {},
      p: {}
    ,
     rules: [
        value => !!value || 'Required.',
        value => (value && value.length <= 500) || 'Max 500 characters',
      ],
    }),
    created() {
      let uri = 'http://localhost:4000/posts';
      this.axios.get(uri).then(response => {
        this.posts = response.data;
      });
    },
    methods: {
   addPost(){
    let uri = 'http://localhost:4000/posts/add';
    this.axios.post(uri, this.p).then(() => {
       this.$router.push({name: 'posts'});
        });
      }
    }
  }
</script>