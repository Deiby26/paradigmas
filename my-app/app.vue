<template>
  <v-app>
    <div style="background-image: url(https://e1.pxfuel.com/desktop-wallpaper/14/125/desktop-wallpaper-2560x1440-marvel-vs-dc-1440p-resolution-backgrounds-and-dc-marvel.jpg); background-attachment: fixed; background-size: cover;">
      <v-container v-for="personaje in personajes" :key="personaje.id" style="height: 900px; width: 900px;" >
        <v-card >
          <center>
            <v-img
            :src="
              personaje.thumbnail.path + '.' + personaje.thumbnail.extension
            " style="height: 420px; width: 420px;"
          >
          </v-img>

          </center>

          <center>
            <br>
            <h3 class="ml-4" style="color: white;"> {{ personaje.name }}</h3>
          </center>
          
          <h4 class="ml-4" v-if="personaje.description !=='' ">Descripción= {{ personaje.description }}</h4>

          <br />
          <div >
            <p>Comics= {{ personaje.comics.available }}</p>
            <p>Eventos= {{ personaje.events.available }}</p>
            <p>Historietas= {{ personaje.stories.available }}</p>
            <p>Series= {{ personaje.series.available }}</p>
          </div>

          <v-divider></v-divider>
          <center>
            <h3 class="ml-4">
            Nombre de las primeras 3 series
            <br />
        </h3>

          </center>

          <br />
          <center>
            <v-card-text v-for="item in personaje.series.items.slice(0, 3)" :key="item">
              {{ item.name }}
            </v-card-text>
        </center>
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
    'http://gateway.marvel.com/v1/public/characters?ts=26&apikey=c898379647e8dbed750931a270b708fc&hash=c21065944a15723aab0dbef097e33db2'
    
    axios
      .get(url)
      .then((response) => (this.personajes = response.data.data.results))
  },
}
</script>

 <style>
  p{margin-top: -20px; margin-left: 16px;}
</style>