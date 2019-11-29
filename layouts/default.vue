<template>
  <v-app dark>
    <v-content>
      <v-container>
        <nuxt />
      </v-container>
    </v-content>
    <v-footer app>
      <v-spacer></v-spacer>
      <a :href="tc">
        <span> Terms and Conditions </span>
      </a>
      <!-- <span>&copy; 2019</span> -->
      <v-spacer></v-spacer>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      items: [
        {
          icon: 'mdi-apps',
          title: 'Welcome',
          to: '/'
        }
      ],
      title: 'Verify your account',
      tc: 'https://telexai.com/docs/TelexAI-Terms-Of-Use.pdf'
    }
  }
}
</script>
