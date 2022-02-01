<template>
  <div id="app">
    <header-box
    :genres="genresList"
    :artists="artistsList"
    @filterGenre="filteredGeneresResults"
    @filterArtist="filteredArtistsResults"
    />
    <!-- LOADER -->
    <loader-element v-if='!loaded'/>
    <main-content v-else :cards='filteredDisks'/>
  </div>
</template>

<script>
import axios from 'axios'
import HeaderBox from './components/HeaderBox.vue'
import LoaderElement from './components/LoaderElement.vue'
import MainContent from './components/MainContent.vue'

export default {
  name: 'App',
  components: {
    HeaderBox,
    LoaderElement,
    MainContent,
  },
  data(){
    return {
      disks: [],
      filteredDisks: [],
      loaded: false,
      genresList: [],
      artistsList: [],
    }
  },
  mounted(){
    // SET AN INTERVAL TO SHOW THE LOADER
    setTimeout(() => {
      // SET THE API CALL
      axios.get('https://flynn.boolean.careers/exercises/api/array/music').then((result) => {
        this.disks = result.data.response;
        this.filteredDisks = result.data.response;
        this.loaded = true;

        // GENERES LIST
        this.disks.forEach((element) => {
          if(!this.genresList.includes(element.genre)){
            this.genresList.push(element.genre);
          }
        })

        // ARTISTS LIST
        this.disks.forEach((element) => {
          if(!this.artistsList.includes(element.author)){
            this.artistsList.push(element.author);
          }
        })
      })
    }, 1000)
  },
  methods: {
    filteredGeneresResults(selection) {
      this.filteredDisks = this.disks.filter((disk) => {
        return disk.genre.includes(selection);
      })
    },
    filteredArtistsResults(selection) {
      this.filteredDisks = this.disks.filter((disk) => {
        return disk.author.includes(selection);
      })
    }
  }
}
</script>

<style lang="scss">
@import './style/main.scss';
</style>
