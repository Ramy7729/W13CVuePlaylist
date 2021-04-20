<template>
  <div class="listCard">
  <!--This for loop cycles through the song list and displays the selected songs by the user. -->
    <div  
      v-for="song in songList"
      :key="song.id"
    > <!-- The selected songs are displayed on the page by accessing their values -->
      <h2> {{ song.title }} </h2>
      <h3> {{ song.artist }} </h3>
    </div>
  </div> 
</template>

<script>
// Registering the component and it's property.
export default {
  name: 'play-list',
  // songList will have data passed down to it from the parent (PageBody.vue).
  props: {
      songList: Object
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.listCard {
  display: grid;
  padding: 3px 26px;
  border-radius: 7px;
  row-gap: 7px;
}
</style>
