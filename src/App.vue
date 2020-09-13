<template>
  <v-app>
    <v-app-bar
      app
      color="blue-grey darken-4"
      dark
    >
    <h1>BMI Calculator</h1>
    </v-app-bar>

    <v-main>
      <HelloWorld/>
    </v-main>
  </v-app>
</template>

<script>
import HelloWorld from './components/HelloWorld';

export default {
  name: 'App',

  components: {
    HelloWorld,
  },

  data: () => ({
    //
  }),
};
</script>
