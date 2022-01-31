<template>
    <main class="container">
        <!-- CARDS -->
        <div class="row">
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
    </main>
</template>

<script>
import CardBox from './CardBox.vue'

export default {
  components: {
    CardBox,
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