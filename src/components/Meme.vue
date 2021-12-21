<template>
  <div class="meme">
    <button class="btn-primary" v-on:click="greet">Another one</button>
    <h1>Kanye West : {{msgK}}</h1>
    <img alt="Meme" :src="img" width="500" height="600">
   
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'Meme',
  props: {
    msgK: String,
    msgT: String,
    img: String
  },
  mounted () {
    this.greet()

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
    
  }
}
}
</script>
