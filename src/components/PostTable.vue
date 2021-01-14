<template>
  <div>
    <v-text-field
      label="Title"
      :rules="rules"
      hide-details="auto"
    ></v-text-field>
    <v-text-field label="Message"></v-text-field>
    <v-btn
    elevation="2"
    fab
    >
    <v-icon>mdi-plus</v-icon>
    </v-btn>
  </div>
</template>

<script>
  export default {
      name: 'PostTable',

    data: () => ({
      rules: [
        value => !!value || 'Required.',
        value => (value && value.length <= 500) || 'Max 500 characters',
      ],

    }),
    methods: {
   addPost(){
    let uri = '//localhost:4000/posts/add';
    this.axios.post(uri, this.post).then(() => {
       this.$router.push({name: 'posts'});
    });
   }
  }
  }
</script>