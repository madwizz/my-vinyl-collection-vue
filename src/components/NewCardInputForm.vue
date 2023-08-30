<template>
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
</template>

<script>
export default {
  
}
</script>

<style>

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