<!-- Collaborated with Liz for this assignment -->
<template>
  <main>
    <h1 class="mrgTopBtm" > The Bestest Playlist in Teh Whole of The Universe</h1>
    <div class="gridSplit" >
    <div>
      <section class="songListContainer" >
        <h2>SONGS</h2>
        <div class="underlineBorder1" ></div>
        
        <!-- The updatePlayList is listening to the emitted event and acts upon it as needed.
          It calls the addSong function with the song that the user selected and
          adds them to the playlist.  
        -->

        <!-- The songList props is referenced  and binded with a list of song objects on this component. 
          It passes down the songList props data to display and emit an event on the child component.
          The update happening is the users selected song choice which is added to the playlist. The update happens
          in PageBody not in the SongList component.
         -->
        <song-list
        @updatePlayList="addSong"
           
        :songList="songList"
        />
      </section>
    </div>  
    <div>  
      <section class="playListContainer">
        <h2 class="listColor"  >PLAY LIST</h2>
        <div class="underlineBorder2"  ></div>
        
        <!-- ADDING SONGS DATA TO THE PLAYLIST -->
        
        <!-- The songList props is referenced and binded with data called songSelection -->
        <!-- songSelection is assigned an empty array object ([]) which gets populated with songs
          specified by the user.
         -->
        <play-list 
          :songList="songSelection"
        />
      </section>
    </div>
    </div>    
</main>  
</template>

<script>
// Importing the components.
import SongList from "./SongList.vue"
import PlayList from "./PlayList.vue"

export default {
  
  name: 'page-body',
  // Registering the sub-components.
  components: {
    SongList,
    PlayList,
  },
  
  // CARRYING OUT SONG TASKS 
  // 1. REMOVING SONGS
  // 2. ADDING SONGS TO THE PLAYLIST
  methods: {
    addSong: function(song) {
      console.log(`adding song:${song}`);
      // The filter method is used to remove the selected song from the song list.
      // The songList is updated with a new list containing songList with the song removed.
      // This is done with the filter method, which will call our passed in function with each item of song list.
      // If the passed in function returns true we keep the song in the list. Else we remove the song from the list.
      this.songList = this.songList.filter(function(songItem) {return songItem !== song;});
       // The push method adds the selected song to the playlist(songSelection []).
      this.songSelection.push(song);
    }
  },
    
    data() {
    return {
    // The songSelection variable is assigned an empty array that will be binded to the props object.
    songSelection: [],
    // This variable stores all of the song information.
      songList: [

        {
          id: 1,
          title: "Prelude/The Sound of Music",
          artist: "Julie Andrews",
        },
        {
          id: 2,
          title: "Piano Concerto No.1, Op.23",
          artist: "Tchaikovsky, perf by. Martha Argerich",
        },
        {
          id: 3,
          title: "Renegade",
          artist: "Jay-Z ft.Eminem",
        },
        {
          id: 4,
          title: "McFearless",
          artist: "Kings of Leon",
        },
        {
          id: 5,
          title: "Your New Morning Alarm",
          artist: "Marc Rebillet",
        },
        {
          id: 6,
          title: "Nocturne in C Sharp Minor No.20, Op.Posth",
          artist: "Chopin, perf. by Wladyslaw Szpilman ",
        },
        {
          id: 7,
          title: "The Black Keys",
          artist: "Aeroplane Blues",
        },
        
      ]
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

@import url('https://fonts.googleapis.com/css2?family=Courgette&display=swap');

* {
  margin: 0;
  padding: 0;
}

.gridSplit {
  display: grid;
  grid-template-columns: 1fr 1fr;
  height: 100vh;
 
  
}

h1 {
  font-family: 'Courgette', cursive;
  margin-bottom: 20px;
  color: white;
 
}

h2 {
  margin-top: 20px;
  margin-bottom: 20px;
  color: white;
}

.songListContainer {
  max-width: 777px;
  margin: 0 auto;
 color: white;
  
}

.listColor {
  color: yellow;
}

.playListContainer {
  max-width: 777px;
  margin: 0 auto;
  color: yellow;
}  

.mrgTopBtm {
  margin-top: 20px;
  margin-bottom: 20px;
}

.underlineBorder1 {
  height: 7px;
  width: 70px;
  background-color: greenyellow;
  margin: 0 auto;
}

.underlineBorder2 {
  height: 7px;
  width: 70px;
  background-color: greenyellow ;
  margin: 0 auto;
  
}
</style>
