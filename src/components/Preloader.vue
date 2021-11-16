<template>
  <transition name="fade">
      <div v-if="show" class="flex flex-col items-center justify-center absolute w-full h-full bg-white z-50">
        <div class="flex items-center justify-center">
            <img src="Spotify_Logo_Black.png" class="w-64 mb-3" />
            <h1 class="text-4xl text-light font-extrabold tracking-widest text-center">-Clone</h1>
        </div> 
        <img class="preloader" src="preloader.gif"/>
      </div>
  </transition>
</template>

<script>
export default {
    name: 'preloader',
    data(){
        return{
            show: true
        }
    },
    mounted(){
        this.showToggle()
    },
    methods: {
        showToggle(){
            setTimeout(() => {
                this.show = false
            }, 7000)
        }
    }
}
</script>


<style>
.fade-enter-active, .fade-leave-active {
    transition: opacity 1s;
}

.fade-enter, .fade-leave-to {
    transition: opacity 3s;
    opacity: 0;
}
</style>


