<template>
  <div  class="bg-dark  h-screen">
    <preloader/>
    <div class="flex" style="height: 88vh">
      <!-- Side nav -->
      <div class="side-bar bg-black h-full flex-none">
        <div class="p-8">
          <img src="Spotify_Logo_Black.png" class="logo" style="filter: brightness(0) invert(1);" />
        </div>

        <div class="mx-5 mb-10">
          <button v-for="page in pages" :key="page.id" @click="setID = page.id" :class="`w-full rounded page px-3 py-2 flex items-center justify-start ${setID === page.id ? 'bg-light  text-white' : ' text-lightest'}`">
            <i class="material-icons mr-3 text-4xl"> {{page.icon}} </i>
            <p class=""> {{page.name}} </p>
          </button>
        </div>

        <div class="mx-5">
            <h1 class="mb-5 mx-4 text-sm text-lightest tracking-widest uppercase">playlists</h1>
            <button class="flex mx-3 items-center justify-start opacity-75 hover:opacity-100 mb-5">
              <img src="addBox.png" class="h-10 w-10 mr-5"/>
              <p class="text-lg text-white font-semibold">Create Playlist</p>
            </button>
            <button class="flex mx-3 items-center justify-start opacity-75 hover:opacity-100">
              <img src="like.png" class="mx-1 h-8 w-8 mr-5" style="filter: brightness(0) invert(1);"/>
              <p class="text-lg text-white font-semibold">Liked Songs</p>
            </button>
            <div class="h-px w-full bg-light my-6 mx-4"></div>
        </div>

        <div class="mx-9">
          <div class="w-full h-24 overflow-y-scroll ">
            <div v-for="album in albums" :key="album.name" class="flex items-center justify-start text-xl">
              <p  class="text-lightest hover:text-white py-2 mr-3"> {{ album.name}} </p>
              <i class="material-icons  text-lg text-white ">{{ album.icon }}</i>
            </div>
          </div>
        </div>
        <button class="flex items-center justify-start text-lightest hover:text-white py-5 mx-9 my-4">
            <i class="material-icons mr-3 text-2xl">downloading</i>
            <p class="text-lg font-semibold">Install App</p>
        </button>

      </div>

      <!-- main content -->
      <div class="w-full h-full relative overflow-y-scroll ">
        <!-- header -->
        <div class="w-full sticky top-0 px-6 py-4 flex items-center justify-between bg-purple shadow-lg z-10">
            <div class="flex items-center mx-4">
              <button class="rounded-full bg-black w-12 h-12 text-white mr-5  "><i class="material-icons text-3xl">keyboard_arrow_left</i></button>
              <button class="rounded-full bg-black w-12 h-12 text-white "><i class="material-icons text-3xl">keyboard_arrow_right</i></button>
            </div>
            <div class="relative">
              <button @click="toggleDropdown" class="bg-black rounded-full py-2 px-1 flex items-center ">
                <img src="singer2.png" class="h-9 w-9 mr-2 rounded-full" />
                <p class="text-white font-semibold text-lg mr-3 ">Tobisam</p>
                <i v-if="showDropdown === false" class="material-icons text-white">arrow_drop_down</i>
                <i v-if="showDropdown === true" class="material-icons text-white">arrow_drop_up</i>

              </button>
              <div v-if="showDropdown === true" class="profile absolute bg-light w-64 mr-14 rounded mt-3">
                <button  @click="showDropdown = false" class="w-full flex items-center justify-between text-lg px-6 py-3 text-white hover:  hover: ">
                  <p>Account</p>
                  <i class="material-icons text-2xl">launch</i>
                </button>
                <button  @click="showDropdown = false" class="w-full flex items-center justify-items-start text-lg px-6 py-3 text-white hover:  hover: ">Profile</button>
                <button  @click="showDropdown = false" class="w-full flex items-center justify-between text-lg px-6 py-3 text-white hover:  hover: ">
                  <p>Upgrade to Premium</p>
                  <i class="material-icons text-2xl">launch</i>
                </button>
                <button  @click="showDropdown = false" class="w-full flex items-center justify-items-start text-lg px-6 py-3 text-white hover:  hover: ">Log out</button>
                
              </div>
            </div>
        </div>

        <!-- cards -->

        <div class="card px-6 py-3">
            <div class="pl-2">
              <h1 class=" text-3xl font-semibold text-white tracker-wider hover:underline pb-3 ">The Top Podcasts of 2021</h1>
              <h2 class="text-lg text-lightest" >Our favorite new shows of the year</h2>
            </div>
            <div class="w-full parent">
              <div v-for="recent in recents" :key="recent.title" class="p-2 w-48 child md:w-60 md:h-auto relative">
                <div class="absolute w-full h-full flex items-end justify-end p-8 opacity-0 hover:opacity-100">
                  <div class="bg-green rounded-full h-12 w-12 flex item-center p-1 justify-center">
                    <i class="material-icons text-white text-4xl">play_arrow</i>
                  </div>
                </div>
                <div class="bg-light w-full h-full p-5 rounded-lg shadow hover:bg-light transition duration-500 ">
                  <img :src="`${ recent.src }`" class="h-36 w-full rounded transition-shadow shadow mb-2 md:h-60"/>
                  <h1 class="text-sm md:text-xl font-semibold text-white tracking-wide">{{ recent.title }}</h1>
                  <h2 class="text-xs md:text-sm text-lightest tracking-wide pb-5">{{ recent.artist}}</h2>
                </div>
              </div>
            <div/>
          </div>
        </div>

        <div class="card px-6 py-3">
            <div class="pl-2">
              <h1 class=" text-3xl font-semibold text-white tracker-wider hover:underline ">Made For Tobisam</h1>
            </div>
            <div class="w-full parent">
              <div v-for="custom in customs" :key="custom.title" class="p-2  w-48 child md:w-60 md:h-auto relative">
                <div class="absolute w-full h-full flex items-end justify-end p-8 opacity-0 hover:opacity-100">
                  <div class="bg-green rounded-full h-12 w-12 flex item-center p-1 justify-center">
                    <i class="material-icons text-white text-4xl">play_arrow</i>
                  </div>
                </div>
                <div class="bg-light w-full h-full p-5 rounded-lg shadow hover:bg-light transition duration-500 ">
                  <img :src="`${ custom.src }`" class="h-36 w-full rounded transition-shadow shadow mb-2 md:h-60"/>
                  <h1 class="text-sm md:text-xl font-semibold text-white tracking-wide">{{ custom.title }}</h1>
                  <h2 class="text-xs md:text-sm text-lightest tracking-wide pb-5">{{ custom.artist}}</h2>
                </div>
              </div>
            <div/>
          </div>
        </div>

        <div class="card px-6 py-3">
            <div class="pl-2">
              <h1 class=" text-3xl font-semibold text-white tracker-wider hover:underline pb-3 ">Appears</h1>
              <h2 class="text-lg text-lightest" >Our favorite new shows of the year</h2>
            </div>
            <div class="w-full parent">
              <div v-for="single in singles" :key="single.title" class="p-2 w-48 child md:w-60 md:h-auto relative">
                <div class="absolute w-full h-full flex items-end justify-end p-8 opacity-0 hover:opacity-100">
                  <div class="bg-green rounded-full h-12 w-12 flex item-center p-1 justify-center">
                    <i class="material-icons text-white text-4xl">play_arrow</i>
                  </div>
                </div>
                <div class="bg-light w-full h-full p-5 rounded-lg shadow hover:bg-light transition duration-500 ">
                  <img :src="`${ single.src }`" class="h-36 w-full rounded transition-shadow shadow mb-2 md:h-60"/>
                  <h1 class="text-sm md:text-xl font-semibold text-white tracking-wide">{{ single.title }}</h1>
                  <h2 class="text-xs md:text-sm text-lightest tracking-wide pb-5">{{ single.artist}}</h2>
                </div>
              </div>
            <div/>
          </div>
        </div>

        <div class="card px-6 py-3">
            <div class="pl-2">
              <h1 class=" text-3xl font-semibold text-white tracker-wider hover:underline pb-3 ">More of what you like</h1>
              <h2 class="text-lg text-lightest" >Hear a little bit of everything you love.</h2>
            </div>
            <div class="w-full parent-appear">
              <div v-for="appear in appears" :key="appear.title" class="p-2 w-48 child-appear md:w-72 md:h-auto relative">
                <div class="absolute w-full h-full flex items-end justify-end p-8 opacity-0 hover:opacity-100">
                  <div class="bg-green rounded-full h-12 w-12 flex item-center p-1 justify-center">
                    <i class="material-icons text-white text-4xl">play_arrow</i>
                  </div>
                </div>
                <div class="bg-dark w-full h-full p-5 rounded-lg shadow transition duration-500 ">
                  <img :src="`${ appear.src }`" class="h-36 w-full rounded transition-shadow shadow mb-2 md:h-60"/>
                  <h1 class="text-sm md:text-xl font-semibold text-white tracking-wide">{{ appear.title }}</h1>
                  <h2 class="text-xs md:text-sm text-lightest tracking-wide pb-5">{{ appear.artist}}</h2>
                </div>
              </div>
            <div/>
          </div>
        </div>
    </div>
  </div>
    <!-- play bar -->
    <div class="w-full flex items-center justify-between px-6 bg-light border-t border-dark shadow-2xl" style="height: 12vh">
      <div class="flex items-center" style="width: 25%">
        <div>
          <h1 class="text-lg text-white tracking-wide">My baby bad and good - Feyisayo</h1>
          <h2 class="text-sm text-lightest tracking-wide">The Carin' Singer</h2>
        </div>
        <i class="material-icons text-xl text-green mx-5">favorite</i>
        <i class="material-icons text-xl text-lightest ">picture_in_picture_alt</i>
      </div>

      <div class="flex flex-col justify-center -mt-1 items-center" style="width: 50%">
        <div class="flex items-center">
          <button class=" text-lightest hover:text-white mx-6"><i class="material-icons text-lg">shuffle</i></button>
          <button class="text-lg text-lightest hover:text-white"><i class="material-icons text-lg">skip_previous</i></button>
          <button @click.prevent="playSong('Fave.mp3')" class="text-lg text-lightest hover:text-white mx-6"><i v-if="pause === false" class="text-4xl material-icons">play_circle_outline</i><i v-if="pause === true" class=" text-4xl material-icons">pause</i></button>
          <button class="text-lg text-lightest hover:text-white"><i class="material-icons text-lg">skip_next</i></button>
          <button class="text-lg text-lightest hover:text-white mx-6"><i class="material-icons text-lg">repeat</i></button>
        </div>
        <div class="flex items-center" style="width: 75%">
          <p class="text-sm text-lightest mr-1">0:28</p>
          <div class="w-full h-1 bg-gray-500 rounded-full flex items-center">
            <div class="h-1 rounded-full bg-green" style="width: 18%"></div>
            <div class="h-3 w-3 bg-white rounded-full -ml-1 shadow"></div>
          </div>
          <p class="text-sm text-lightest ml-1">2:58</p>
        </div>
      </div>

      <div class="flex items-center justify-end" style="width: 25%">
        <i class="material-icons text-lightest hover:text-white">playlist_play</i>
        <i class="material-icons text-xl mx-3 text-lightest hover:text-white">important_devices</i>
        <i class="material-icons text-xl text-lightest hover:text-white">volume_up</i>
        <div class="w-28 ml-1 bg-lightest rounded-full h-1 hover:bg-green"></div>
      </div>
    </div>
    
  </div>
</template>

<script>

import Preloader from './components/Preloader.vue'

export default {
  components: {
    Preloader
  },
  name: 'App',
  data() {
    return {
      pages: [
        {id: 'home', name: 'Home', icon: 'home'},
        {id: 'search', name: 'Search', icon: 'search'},
        {id: 'library', name: 'Your Library', icon: 'bar_chart'}
      ],
      setID: 'home',
      albums: [
        {name: 'drive', icon: 'headphones'},
        {name: 'zhu', icon: 'headphones'},
        {name: 'All New Indie', icon: 'headphones'},
        {name: 'Mellow', icon: 'headphones'},
        {name: 'Classic Road Trip Songs', icon: 'headphones'},
        {name: 'Jolly Radio', icon: 'headphones'},
        {name: 'Lana Del Rey Radio', icon: 'headphones'},
        {name: 'B. Bush 1997 Radio', icon: 'headphones'},
        {name: 'L.Havard 2009 Radio', icon: 'headphones'},
        {name: 'Lana 1999 Radio', icon: 'headphones'},
        {name: 'Lana Huston Radio', icon: 'headphones'},
        {name: 'Lana Del Geoge', icon: 'headphones'},
        {name: 'Fidelity Radio', icon: 'headphones'},
        {name: 'D. Lang Film', icon: 'headphones'}
      ],
      showDropdown: false,
      recents: [
        {src: 'song1.png', title: 'Daily Mix 1', artist: 'By Spotify'},
        {src: 'song2.jpeg', title: 'Kiss me ', artist: 'By Yinka'},
        {src: 'singer3.png', title: 'Daily food', artist: 'By Spotify'},
        {src: 'playing.png', title: 'My baby bad', artist: 'By Spotify'}
      ],
      singles: [
        {src: 'singer1.png', title: 'Life is good', artist: 'By Billie'},
        {src: 'singer2.png', title: 'Daily Mix 3', artist: 'By Frank'},
        {src: 'artist1.jpg', title: 'God Ever 3', artist: 'By JOhn H'},
        {src: 'artist2.jpg', title: 'My baby', artist: 'By Spotify'}
      ],
      customs: [
        {src: 'artist10.jpg', title: 'Its God', artist: 'By Spotify'},
        {src: 'artist6.jpg', title: 'Oner of life', artist: 'By Yinka'},
        {src: 'artist1.jpg', title: 'Daily bread', artist: 'By Spotify'},
        {src: 'artist3.jpg', title: 'My baby good', artist: 'By Billie'}
      ],
      appears: [
        {src: 'artist4.jpg', title: 'Baddo 3', artist: 'By Frank'},
        {src: 'artist5.jpg', title: 'God', artist: 'By JOhn H'}
      ],
      pause: false
    }
  },
  mounted(){
    window.addEventListener('click', this.close)
  },

  beforeUnmount(){
    window.removeEventListener('click', this.close)
  },
  methods: {
    toggleDropdown() {
      this.showDropdown = !this.showDropdown;
    },

    close(e) {
      if(!this.$el.contains(e.target)) {
        this.showDropdown = false
      }
    },
    playSong(song) {
      if (song){
        var audio = new Audio(song);
        audio.play();
      } 
      
        
      // audio = new Audio(song);
      // audio.pause;
      // audio.currentTime = 0;
      
      this.pause = !this.pause;

    }
  }
 


}
</script>

<style scoped>
.side-bar{
  width: 270px
}
.side-bar .logo {
  height: 40px;
}
.side-bar .page{
  font-size: 12px;
  font-weight: 600; 
}

.card .parent{
  display: flex;
  flex-wrap: wrap;
  margin: 10px 0 0 -10px;
}
.card .parent .child{
  display: inline-block;
  margin: 10px 0 0 10px;
  flex-grow: 1;
}
.card .parent-appear{
  display: flex;
  flex-wrap: wrap;
  margin: 10px 0 0 -10px;
}
.card .parent .child-appear{
  display: inline-block;
  margin: 10px 0 0 10px;
  flex-grow: 1;
}
.profile{
  right: -40px;
}


</style>

