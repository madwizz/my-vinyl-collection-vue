<script>
  export default {
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
      addLike(card) {
        if (card.likes === null) {
          card.likes = 1
        } else {
          card.likes += 1
        }
      },
      removeLike(card) {
        if (card.likes !== null && card.likes > 0) {
          card.likes -= 1
        }
      },
      createCard() {
        const newCard = {
          id: Date.now(),
          albumName: this.albumName,
          bandName: this.bandName,
          albumCoverUrl: this.albumCoverUrl,
        }
        this.cards.push(newCard)
        this.albumName = ''
        this.bandName = ''
        this.albumCoverUrl = ''
      },

    }
  }
</script>

<template>
  <div class="page">
    <header class="header">
      <form
        @submit.prevent
        class="input-group">
        <input
          v-model="albumName"
          @input="albumName = $event.target.value"
          class="input" 
          type="text" 
          placeholder="album name">
        <input
          v-model="bandName"
          @input="bandName = $event.target.value"
          class="input" 
          type="text" 
          placeholder="band name">
        <input
          v-model="albumCoverUrl"
          class="input" 
          type="text" 
          placeholder="album cover url">
        <v-btn 
          class="v-btn" 
          icon="mdi-plus" 
          size="small" 
          color="black" 
          @click="createCard" >
        </v-btn>
      </form>
    </header>
    <div class="v-cards-grid">
      <v-card
        v-for="card in cards"
        :key="card.id"
        variant="outlined">
          <v-card-title>{{ card.albumName }}</v-card-title>
          <v-card-subtitle class="v-card-subtitle">{{ card.bandName }}</v-card-subtitle>
          <v-img
            :width="400"
            aspect-ratio="16/9"
            cover
            :src="card.albumCoverUrl">
          </v-img>
          <v-card-actions class="v-card-actions">
            <v-btn 
                class="ma-2"
                variant="text"
                icon="mdi-thumb-up"
                color="blue-lighten-2"
                @click="addLike(card)">
            </v-btn>
            <div>{{ card.likes }}</div>
            <v-btn 
              class="ma-2"
              variant="text"
              icon="mdi-thumb-down"
              color="red-lighten-2"
              @click="removeLike(card)">
            </v-btn>
          </v-card-actions>
      </v-card>
    </div>
  </div>

</template>

<style>
  .page {
    display: grid;
    grid-template-areas: 
    "header"
    "v-cards-grid v-cards-grid v-cards-grid";
    gap: 10px;
  }

  .header {
    display: grid;
    grid-area: "header";
    justify-content: center;
  }

  .input-group {
    display: flex;
    flex-direction: row;
    gap: 10px;
  }
  
  .input {
    border: 1px white solid;
    color: white;
  }

  .v-cards-grid {
    display: grid;
    grid-area: "v-cards-grid";
    grid-template-columns: repeat(2, 1fr);
    grid-template-rows: repeat(2, 1fr);
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
