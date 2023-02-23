<template>
    <div id="app"> 
      <NavBar></NavBar>
      <!-- <IPhone></IPhone> -->
      <DeTail></DeTail>
      <!-- <IPhone></IPhone> -->
      <!-- <PopUp></PopUp> -->
    </div>
    
</template>

<script>
import NavBar from './components/NavBar.vue';
// import IPhone from './components/IPhone.vue';
import DeTail from './components/DeTail.vue';
// import PopUp from './components/PopUp.vue'; 

export default {
  name: 'App',
  components: {
    NavBar,DeTail
  },

}
</script>

<style>

@font-face {
    font-style: normal;
    font-family: 'Sukhumvit Set';
    src: local("Sukhumvit Set"),
    url('@/assets/SukhumvitSet-Text.ttf');
}

#app{
  /* font-family: 'Sukhumvit Set';
  font-style: normal; */
  /* font-family: 'Sukhumvit set' */
}


</style>
