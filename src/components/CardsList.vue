<template>
  <div v-if="cards.length > 0" class="v-cards-grid">
    <card-item
    class=""
    :key="card.id" 
    v-for="card in cards"
    :card="card"
    @removeCard="$emit('removeCard', card)"/>
  </div>
  <h2 class="heading" v-else>Your shelf looks empty. Add some of your records!</h2>
</template>

<script>
  import CardItem from './CardItem.vue'
  export default {
    components: {CardItem},
    props: {
      cards: {
        type: Array,
        required: true,
      }
    }
  }
</script>

<style scoped>

.v-cards-grid {
    display: grid;
    grid-area: "v-cards-grid";
    grid-template-columns: repeat(3, 1fr);
    grid-template-rows: repeat(3, 1fr);
    grid-column-gap: 30px;
    grid-row-gap: 30px;
  }

  .v-card-subtitle {
    padding-bottom: 1rem;
  }

  .v-card-actions {
    justify-content: center;
  }
  
</style>