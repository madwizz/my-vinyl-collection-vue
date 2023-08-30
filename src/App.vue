<script>
  import CardForm from "./components/CardForm.vue"
  import CardsList from "./components/CardsList.vue"
  export default {
    components: {
      CardForm, CardsList,
    },
    data() {
      return {
        cards: [
          {
            id: 1, 
            albumName: 'the slab', 
            bandName: 'Slowdive', 
            albumCoverUrl: 'https://static.stereogum.com/uploads/2023/08/82dd7fcd-1cfd-1457-bfa7-f3e943f6d342-1691501528.jpg', 
            likes: null,
          },
          {
            id: 2, 
            albumName: 'skin in the game', 
            bandName: 'Slowdive', 
            albumCoverUrl: 'https://i.scdn.co/image/ab67616d0000b273f92dc426a8eb3c5128a1a641', 
            likes: null,
          },
          {
            id: 3, 
            albumName: 'kisses', 
            bandName: 'Slowdive', 
            albumCoverUrl: 'https://media.pitchfork.com/photos/64919a8037e30e506f0411ce/1:1/w_450%2Cc_limit/Slowdive-Kisses.jpg', 
            likes: null,
          },
          {
            id: 4, 
            albumName: 'everything is alive', 
            bandName: 'Slowdive', 
            albumCoverUrl: 'https://f4.bcbits.com/img/a3812998304_65', 
            likes: null,
          },
          
        ]
      }
    },
    methods: {

      createCard(card) {
        this.cards.push(card)
      },
      removeCard(card) {
        this.cards = this.cards.filter(c => c.id !== card.id)
      }

    }
  }
</script>

<template>
  <div class="page">
    <h1 class="heading">My Vinyl Collection</h1>
    <header class="header">
      <card-form 
        @createCard="createCard"/>
    </header>
      <cards-list  
        :cards="cards"
        @removeCard="removeCard"/>
  </div>

</template>

<style>
  .page {
    display: grid;
    grid-template-areas: 
    "header"
    "v-cards-grid v-cards-grid v-cards-grid";
    gap: 15px;
  }

  .header {
    display: grid;
    grid-area: "header";
    justify-content: center;
  }

  .heading {
    display: flex;
    justify-content: center;
  }

</style>
