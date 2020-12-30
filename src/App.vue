<template>
  <div class = 'container my-5'>
    
    <cocktail class="align-middle"/>
    <video playsinline autoplay muted loop>
      <source src="./assets/bg-bar.mp4">
    </video>
  </div>
</template>

<script>

import cocktail from "./components/cocktail.vue"
export default {
  name: 'App',
  components: {
    cocktail
  }
}
</script>

<style>
/*
html,body{
  background-color: darkgray;
}*/
html{

}
video
{
  object-fit:cover;
  width: 100vw;
  height:100vh;
  position:fixed;
  top:0;
  left:0;
  z-index: -100;
}
</style>
