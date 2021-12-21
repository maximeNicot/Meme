<template>
  <v-app>
    <v-main>
      <Meme/>
    </v-main>
  </v-app>
</template>

<script>
import Meme from './components/Meme';

export default {
  name: 'App',

  components: {
     Meme
  },

  data: () => ({
    //
  }),
};
</script>
