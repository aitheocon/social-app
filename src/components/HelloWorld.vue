<template>
  <v-container>
    <v-row class="text-center">
      <v-col cols="12">
        <v-img
          :src="require('../assets/newlogo.jpg')"
          class="my-3"
          contain
          height="200"
        />
      </v-col>

      <v-col class="mb-4">
        <h1 class="display-2 font-weight-bold mb-3">
          Welcome to SWIFTe...
        </h1>

        <p class="subheading font-weight-regular">
          If you'd like to JUST look, please click
          <a
            href="https://community.vuetifyjs.com"
            target="_blank"
          >here</a>
        </p>
      </v-col>

      <v-col
        class="mb-5"
        cols="12"
      >
        <h2 class="headline font-weight-bold mb-3">
          What's next?
        </h2>

        <v-row justify="center">
          <a
            v-for="(next, i) in whatsNext"
            :key="i"
            :href="next.href"
            class="subheading mx-3"
            target="_blank"
          >
            {{ next.text }}
          </a>
        </v-row>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
  export default {
    name: 'HelloWorld',

    data: () => ({
      whatsNext: [
        {
          text: 'Posts',
          href: 'https://vuetifyjs.com/components/api-explorer',
        },
        {
          text: 'Your Posts',
          href: 'https://vuetifyjs.com/getting-started/pre-made-layouts',
        },
        {
          text: 'Profile',
          href: 'https://vuetifyjs.com/getting-started/frequently-asked-questions',
        },
      ],
    }),
  }
</script>
