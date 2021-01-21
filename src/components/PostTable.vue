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

      <v-toolbar-title>Inbox</v-toolbar-title>

      <v-spacer></v-spacer>

      <v-btn icon>
        <v-icon>mdi-magnify</v-icon>
      </v-btn>
    </v-toolbar>

    <v-list three-line v-for="post in posts" :key="post._id">
        <v-subheader
          v-if="post.author"
          :key="post.author"
          v-text="post.author"
        ></v-subheader>

        <v-divider></v-divider>

        <v-list-item
          :key="post.title"
        >

          <v-list-item-content>
            <v-list-item-title v-html="post.title"></v-list-item-title>
            <v-list-item-subtitle v-html="post.body"></v-list-item-subtitle>
          </v-list-item-content>
          <td><button v-on:click="deletePost(post._id)" class="btn btn-danger">Delete</button></td>
        </v-list-item>
    </v-list>
  </v-card>
  <form @submit.prevent="addPost">
    <v-text-field
      v-model="p.title"
      :counter="10"
      label="Title"
      required
    ></v-text-field>
    <v-text-field
      v-model="p.body"
      label="Message"
      required
    ></v-text-field>
    <v-text-field
      v-model="p.author"
      label="Author"
      required
    ></v-text-field>
    
    <v-btn
      class="mr-4"
      @click="addPost"
    >
      submit
    </v-btn>
  </form>
  </div>
</template>

<script>
  export default {
      name: 'PostTable',

    data: () => ({
      posts: {},
      p: {},
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
       this.$router.push({name: 'Posts'});
        });
      },
      deletePost(id) {
      let uri = 'http://localhost:4000/posts/delete/${id}';
      this.axios.delete(uri).then((response) => {
        this.posts = this.posts.filter((r) => r._id != id);
        console.log(response.data);
      });
    },
  }
  }
</script>