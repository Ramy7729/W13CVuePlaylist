<template>
  <div class="songCard" >
    <!-- The click event enables the user to select a song from the list and add
      it to their playlist.
      The for loop cyles through the songList and displays all of the songs.
    -->
    <div @click="updatePlayList(song)"
    v-for="song in songList"
    :key="song.id" 
    >
      <!-- The songs are displayed on the page by accessing their values -->
      <h2> {{ song.title }} </h2>
      <h3> {{ song.artist }} </h3>
    </div>
  </div>  
</template>

<script>
// Registering the component and it's property.
export default {
  name: 'song-list',
  // songList will have data passed down to it from the parent (PageBody.vue).
  props: {
    songList: Object
  },
  
  // SETTING UP PARENT/CHILD COMMUNICATION TO ENABLE UPDATING OF DATA
  
  methods: {
    // This is a function that emits an update playlist event when a song is clicked.
    // However, for the playlist to update, it must communicate with the parent (PageBody.vue).
    updatePlayList: function(song) {
      this.$emit("updatePlayList", song);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.songCard {
  display: grid;
  padding: 3px 26px;
  border-radius: 7px;
  row-gap: 27px;
}
</style>
