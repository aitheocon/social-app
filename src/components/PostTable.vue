<template>
  <div>
    <v-text-field
      label="Main input"
      :rules="rules"
      hide-details="auto"
    ></v-text-field>
    <v-text-field label="Another input"></v-text-field>
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
        value => (value && value.length >= 3) || 'Max 500 characters',
      ],
    }),
  }
</script>