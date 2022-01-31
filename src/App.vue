<template>
  <div id="app">
    <header-box />
    <main-content :cards='disks'/>
  </div>
</template>

<script>
import axios from 'axios'
import HeaderBox from './components/HeaderBox.vue'
import MainContent from './components/MainContent.vue'

export default {
  name: 'App',
  components: {
    HeaderBox,
    MainContent,
  },
  data(){
    return {
      disks: [],
    }
  },
  mounted(){
    // SET AN INTERVAL TO SHOW THE LOADER
    setInterval(() => {
      // SET THE API CALL
      axios.get('https://flynn.boolean.careers/exercises/api/array/music').then((result) => {
        this.disks = result.data.response
      })
    }, 2000)
  },
}
</script>

<style lang="scss">
@import './style/main.scss';
</style>
