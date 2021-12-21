<template>
  <v-card width="750" class="mx-auto mt-5">
  <v-card-title><h1>Lizafekuni</h1></v-card-title>
  <v-divider></v-divider>
    <h2>Kanye West : {{msgK}}</h2>
    <v-row class="text-center">
      <v-col cols="12">
          <img alt="Meme" :src="img" width="550" height="650">
      </v-col>
    </v-row>
      <v-card-actions>
        <v-btn color="primary" elevation="2" v-on:click="greet">Another one</v-btn>
      </v-card-actions>

      <v-divider></v-divider>

    <h2>If you're bored, you can : {{msgB}}</h2>
    <v-card-actions>
        <v-btn color="primary" elevation="2" v-on:click="boring">Still bored !</v-btn>
      </v-card-actions>
  </v-card>
</template>

<script>
import axios from 'axios'
export default {
  name: 'Meme',
  props: {
    msgK: String,
    msgB: String,
    img: String
  },
  mounted () {
    this.greet()
    this.boring()

  },

  methods: {
    greet: function () {
       const rand = Math.floor(Math.random() * 75)
    axios
      .get('https://api.imgflip.com/get_memes')
      .then(response => {
        //this.msgK = response.data.data.memes[0].name
        this.img = response.data.data.memes[rand].url
        })

    axios
      .get('https://api.kanye.rest/')
      .then(response => {
        this.msgK = response.data.quote
        })
    
  },
  boring: function () {
    axios
      .get('http://www.boredapi.com/api/activity/')
      .then(response => {
        this.msgB = response.data.activity
        })
    
  }
}
}
</script>
