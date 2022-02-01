<template>
    <main class="container">
        <!-- CARDS -->
        <div class="row">
          <card-box
          v-for='(card, index) in cards'
          :key='index'
          :disk="card"
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
</style>