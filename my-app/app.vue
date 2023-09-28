<template>
  <v-app>
    <div>
      <v-container v-for="personaje in personajes" :key="personaje.id">
        <v-card>
          
          <v-img
            :src="
              personaje.thumbnail.path + '.' + personaje.thumbnail.extension
            " 
          >
          </v-img>
          

        </v-card>
      </v-container>
    </div>
  </v-app>
</template>

<script>
import axios from 'axios'

export default {
  name: 'IndexPage',

  data() {
    return {
      personajes: [],
    }
  },
  created() {
    const url =
      'http://gateway.marvel.com/v1/public/characters?ts=8&apikey=&hash='
    
    axios
      .get(url)
      .then((response) => (this.personajes = response.data.data.results))
  },
}
</script>

 <style>
  p{margin-top: -20px; margin-left: 16px;}
</style>