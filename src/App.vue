<template>
  <div  class="bg-dark  h-screen">
    <div class="flex" style="height: 88vh">
      <!-- Side nav -->
      <div class="w-56 bg-black h-full flex-none">
        <div class="p-6">
          <img src="Spotify_Logo_Black.png" class="h-10" style="filter: brightness(0) invert(1);" />
        </div>

        <div class="mx-2 mb-5">
          <button v-for="page in pages" :key="page.id" @click="setID = page.id" :class="`w-full text-sm font-semibold  rounded px-3 py-2 flex items-center justify-start ${setID === page.id ? 'bg-light text-white' : 'text-lightest'}`">
            <i class="material-icons mr-3"> {{page.icon}} </i>
            <p> {{page.name}} </p>
          </button>
        </div>

        <div class="mx-5">
            <h1 class="mb-3 text-xs text-lightest tracking-widest uppercase">playlists</h1>
            <button class="flex items-center justify-start opacity-75 hover:opacity-100 mb-2">
              <img src="addBox.png" class="h-8 w-8 mr-3"/>
              <p class="text-sm text-white font-semibold">Create Playlist</p>
            </button>
            <button class="flex items-center justify-start opacity-75 hover:opacity-100">
              <img src="like.png" class="h-8 w-8 mr-3" style="filter: brightness(0) invert(1);"/>
              <p class="text-sm text-white font-semibold">Liked Songs</p>
            </button>
            <div class="h-px w-full bg-light my-3"></div>
        </div>

        <div class="mx-5">
          <div class="w-full h-10 overflow-y-scroll ">
            <p v-for="album in albums" :key="album.name" class="text-lightest hover:text-white text-xs py-1"> {{ album.name}} </p>

          </div>
        </div>

      </div>

      <!-- main content -->
      <div class="w-full h-full relative">
        <!-- header -->
        <div class="w-full sticky top-0 p-2">

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
      ]
    }
  },
 


}
</script>

<style src="./assets/tailwind.css">

</style>

