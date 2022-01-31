<template>
    <main class="container">
        <!-- CARDS -->
        <div class="row" v-if='cards.length === 10'>
          <card-box
          v-for='(card, index) in cards'
          :key='index'
          :thumb="card.poster"
          :title="card.title"
          :author="card.author"
          :genre="card.genre"
          :year="card.year"
          />
        </div>
        <!-- LOADER -->
        <loader-element v-if='cards.length < 10'/>
    </main>
</template>

<script>
import LoaderElement from './LoaderElement.vue'
import CardBox from './CardBox.vue'

export default {
  components: {
    CardBox,
    LoaderElement,
  },
  props: {
    cards: Array,
  }
}
</script>

<style lang="scss" scoped>
.container{
  padding: 60px 0
}
</style>