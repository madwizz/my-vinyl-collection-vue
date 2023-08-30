<template>
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
</template>

<script>
export default {
  
}
</script>

<style>

  .v-card-subtitle {
    padding-bottom: 1rem;
  }

  .v-card-actions {
    justify-content: center;
  }
  
</style>