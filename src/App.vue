<template>
  <div id="app">
    <header-box />
  </div>
</template>

<script>
import axios from 'axios'
import HeaderBox from './components/HeaderBox.vue'

export default {
  name: 'App',
  components: {
    HeaderBox,
  },
  data(){
    return {
      discs: [],
    }
  },
  mounted(){
    axios.get('https://flynn.boolean.careers/exercises/api/array/music').then((response) => {
      this.discs = response.data;
    })
  },
}
</script>

<style lang="scss">
@import './style/main.scss';

#app {

}
</style>
