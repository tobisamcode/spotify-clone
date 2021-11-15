<template>
  <div  class="bg-dark  h-screen">
    <div class="flex" style="height: 88vh">
      <!-- Side nav -->
      <div class="w-56 bg-black h-full flex-none">
        <div class="p-6">
          <img src="Spotify_Logo_Black.png" class="h-10" style="filter: brightness(0) invert(1);" />
        </div>

        <div class="mx-2 mb-5">
          <button v-for="page in pages" :key="page.id" @click="setID = page.id" :class="`w-full text-sm font-semibold  rounded px-3 py-2 flex items-center justify-start ${setID === page.id ? 'bg-light  text-white' : ' text-lightest'}`">
            <i class="material-icons mr-3"> {{page.icon}} </i>
            <p> {{page.name}} </p>
          </button>
        </div>

        <div class="mx-5">
            <h1 class="mb-3 text-xs text-lightest tracking-widest uppercase">playlists</h1>
            <button class="flex items-center justify-start opacity-75 hover:opacity-100 mb-2">
              <img src="addBox.png" class="h-8 w-8 mr-3"/>
              <p class="text-xs text-white font-semibold">Create Playlist</p>
            </button>
            <button class="flex items-center justify-start opacity-75 hover:opacity-100">
              <img src="like.png" class="h-8 w-8 mr-3" style="filter: brightness(0) invert(1);"/>
              <p class="text-xs text-white font-semibold">Liked Songs</p>
            </button>
            <div class="h-px w-full bg-light my-3"></div>
        </div>

        <div class="mx-5">
          <div class="w-full h-10 overflow-y-scroll ">
            <p v-for="album in albums" :key="album.name" class="text-lightest hover:text-white text-sm py-1"> {{ album.name}} </p>
          </div>
          <button class="flex items-center justify-start text-lightest hover:text-white py-2">
            <i class="material-icons mr-3 rounded-full border border-lightest text-xs">arrow_downward</i>
            <p class="text-sm font-semibold">Install App</p>
          </button>
        </div>
        <div class="relative pt-4 ">
          <div class="w-full h-full flex justify-end items-start opacity-0 hover:opacity-100 absolute p-2">
            <div class="bg-black rounded-full h-6 w-6">
              <i class="material-icons text-white">keyboard_arrow_down</i>
            </div>
          </div>
          <img src="singer1.png" class=" w-full" style="height: 235px" />
        </div>

      </div>

      <!-- main content -->
      <div class="w-full h-full relative overflow-y-scroll ">
        <!-- header -->
        <div class="w-full sticky top-0 px-6 py-4 flex items-center justify-between ">
            <div class="flex items-center">
              <button class="rounded-full bg-black w-8 h-8 text-white mr-3 "><i class="material-icons text-3xl">keyboard_arrow_left</i></button>
              <button class="rounded-full bg-black w-8 h-8 text-white "><i class="material-icons text-3xl">keyboard_arrow_right</i></button>
            </div>
            <div class="relative">
              <button @click="showDropdown = true" class="bg-light rounded-full py-1 px-2 flex items-center ">
                <img src="singer2.png" class="h-6 w-6 mr-2 rounded-full" />
                <p class="text-white font-semibold text-xs mr-3 ">Tobi Samuel</p>
                <i v-if="showDropdown === false" class="material-icons text-white">arrow_drop_down</i>
                <i v-if="showDropdown === true" class="material-icons text-white">arrow_drop_up</i>

              </button>
              <div v-if="showDropdown === true" class="absolute bg-light w-full rounded mt-1">
                <button  @click="showDropdown = false" class="w-full text-sm py-2 text-lightest hover:text-white border-b border-white opacity-50 hover:opacity-100 ">Account</button>
                <button @click="showDropdown = false" class="w-full text-sm py-2 text-lightest hover:text-white ">Log out</button>
              </div>
            </div>
        </div>

        <!-- cards -->
        <div class="px-6 ">
            <div class="px-6 py-3 flex align-items justify-between">
              <h1 class="pl-2 text-2xl font-semibold text-white tracker-wider hover:underline ">Recently Played</h1>
              <h2 class="pr-8 text-xs text-lightest uppercase tracking-wider hover:underline mb-3">See All</h2>
              <div class="w-full flex flex-wrap">
                <div class="p-2 w-48">
                  <div class="bg-light w-full h-auto p-5">
                    <img src="" class="h-auto w-full shadow mb-2"/>
                    <h1 class="text-sm font-semibold text-white tracking-wide"></h1>
                    <h2 class="text-xs text-lightest tracking-wide "></h2>
                  </div>
                </div>
              </div>
            </div>
          
        </div>
      </div>

    </div>
    <!-- play bar -->
    <div class="w-full bg-light" style="height: 12vh">

    </div>
    
  </div>
</template>

<script>



export default {
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
        {name: 'drive'},
        {name: 'zhu'},
        {name: 'All New Indie'},
        {name: 'Mellow'},
        {name: 'Classic Road Trip SOngs'},
        {name: 'Lana Del Rey Radio'}
      ],
      showDropdown: false
    }
  },
 


}
</script>

<style src="./assets/tailwind.css">

</style>

