<template>
  <form
    @submit.prevent
    class="input-group">
    <input
      v-model="card.albumName"
      @input="card.albumName = $event.target.value"
      class="input" 
      type="text" 
      placeholder="album name">
    <input
      v-model="card.bandName"
      @input="card.bandName = $event.target.value"
      class="input" 
      type="text" 
      placeholder="band name">
    <input
      v-model="card.albumCoverUrl"
      class="input" 
      type="text" 
      placeholder="album cover url">
    <input
      v-model="card.spotifyEmbedCode"
      class="input" 
      type="text" 
      placeholder="spotify embed code">
    <v-btn 
      class="v-btn" 
      icon="mdi-plus" 
      size="small" 
      color="black"
      @click="createCard"
      >
    </v-btn>
  </form>
</template>

<script>
export default {
  data() {
    return {
      card: {
        albumName: '',
        bandName: '',
        albumCoverUrl: '',
        spotifyEmbedCode: '',
      },
    }
  },
  methods: {
    createCard() {
      this.card.id = Date.now()
      this.$emit('createCard', this.card)
      this.card = {
        albumName: '',
        bandName: '',
        albumCoverUrl: '',
        spotifyEmbedCode: '',
        likes: null
      }
    },
  }
}
</script>

<style scoped>

  .input-group {
    display: flex;
    flex-direction: row;
    gap: 10px;
  }
  
  .input {
    border: 1px white solid;
    color: white;
  }
  
</style>