<template>
  <div>
    <b-navbar class='navBar' variant="faded" type="light">
      <b-navbar-brand class='nav-brand' href="#">interview</b-navbar-brand>
      <b-navbar-item class='nav-item' href="#">สั่งซื้อล่วงหน้า iPhone 12</b-navbar-item>
    </b-navbar>
  </div>
</template>

<script>
export default {
  name: "NavBar",
};
</script>

<style>
/* @import url('@/assets/SukhumvitSet-Text.ttf') */

@font-face {
    font-style: normal;
    font-family: 'Sukhumvit Set';
    src: local("Sukhumvit Set"),
    url('@/assets/SukhumvitSet-Text.ttf');
}

.navBar{
    border-bottom:1px solid #dad9d9;;
}
.nav-brand{
    font-family: 'Sukhumvit Set';
    color: #5BBA47 !important;
    padding-left: 220px;
    font-weight: bolder;
    font-size: 25px !important;
    line-height: 40px;
}

.nav-item{
    font-style: normal;
    font-family: 'Sukhumvit Set';
    padding-left: 700px;
    font-weight: 600 !important;
    font-size: 20px;
    line-height: 32px;
    font-weight: bolder ;
}

@media screen and (max-width: 833px) {
   
  .nav-item {
    padding-left: 350px;
  }
  .nav-brand{
    padding-left: 30px;
  }
}
</style>
