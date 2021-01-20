<template>
  <v-form
    ref="form"
    v-model="valid"
    lazy-validation
  >
    <v-text-field
      v-model="users.username"
      :counter="10"
      :rules="nameRules"
      label="Username"
      required
    ></v-text-field>

    <v-text-field
      v-model="users.email"
      :rules="emailRules"
      label="E-mail"
      required
    ></v-text-field>

    <v-text-field
      v-model="users.phone"
      :rules="phoneRules"
      label="Phone"
      required
    ></v-text-field>

    <v-checkbox
      v-model="checkbox"
      :rules="[v => !!v || 'Is this your profile?']"
      label="Are you done?"
      required
    ></v-checkbox>

    <v-btn
      :disabled="!valid"
      color="success"
      class="mr-4"
      @click="updateUser"
    >
      Save Changes
    </v-btn>

    <v-btn
      color="error"
      class="mr-4"
      @click="reset"
    >
      Clear Changes
    </v-btn>

  </v-form>
</template>


<script>
  export default {
    data: () => ({
        users: {}
      ,
      valid: true,
      name: '',
      nameRules: [
        v => !!v || 'Username is required',
        v => (v && v.length <= 10) || 'Username must be less than 10 characters',
      ],
      email: '',
      emailRules: [
        v => !!v || 'E-mail is required',
        v => /.+@.+\..+/.test(v) || 'E-mail must be valid',
      ],
      phone: '',
      phoneRules: [
        v => !!v || 'A phone number is required',
        v => (v && v.length == 10) || 'Phone must be valid and unbroken',
      ],
      checkbox: false,

      created() {
      let uri = 'http://localhost:4000/users';
      this.axios.get(uri).then(response => {
        this.users = response.data;
      });
    },
    }),

    methods: {
      validate () {
        this.$refs.form.validate()
      },
      reset () {
        this.$refs.form.reset()
      },
      resetValidation () {
        this.$refs.form.resetValidation()
      },
      updateUser() {
          let uri = `http://localhost:4000/users/update/${this.$route.params.id}`;
          this.axios.post(uri, this.user).then(() => {
            this.$router.push({name: 'Posts'});
          });
        }
    },
  }
</script>