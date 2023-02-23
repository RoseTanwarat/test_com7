<template>
<div class="img-phone">
    <!-- <div v-for="get in getData()" :key="get.id">{{ get }}</div> -->
    <!-- <img src="https://media-cdn.bnn.in.th/140326/iPhone_13_PDP_Position-1A_Color_Pink__1-square_medium.jpg" width="500" height="500" > -->
    <img v-if="image" :key="image.id" @click="switchImage" class="image" :src="image.src" alt="image.alt" width="500" v-bind="image">
</div>
        
</template>

<script>
// import DeTail from './DeTail.vue';
export default {
  name: "IPhone",
  data(){
    return{
      data:'',
      index: 0,
      image: null,
      images: [{
          id: 1,
          src: "https://media-cdn.bnn.in.th/140326/iPhone_13_PDP_Position-1A_Color_Pink__1-square_medium.jpg",
          alt: "Pink",
          
        },
        {
          id: 2,
          src: "https://store.storeimages.cdn-apple.com/8756/as-images.apple.com/is/iphone-13-starlight-select-2021?wid=470&hei=556&fmt=png-alpha&.v=1629907845000",
          alt: "Starlight",
        },
        {
          id: 3,
          src: "https://store.storeimages.cdn-apple.com/8756/as-images.apple.com/is/iphone-13-midnight-select-2021?wid=470&hei=556&fmt=png-alpha&.v=1629907844000",
          alt: "Mid"
        },
        {
          id: 4,
          src: "https://store.storeimages.cdn-apple.com/8756/as-images.apple.com/is/iphone-13-blue-select-2021?wid=470&hei=556&fmt=png-alpha&.v=1629842712000",
          alt: "Blue"
        },
       
      ]
    
    }
  },
  methods:{
    async getData() {
      await fetch('https://interview.com7.in/api/pre-order')
        .then(response => response.json())
        .then((data) => console.log('images',data.data.main_product[0].model[0].data[0].images[0]));
    },
    switchImage() {
      this.image = this.images[this.index];
      this.index = (this.index + 1) % this.images.length;
      // console.log(this.image)
      console.log(this.index)
    }
  },
  mounted() {
      // this.getData();
      this.switchImage();
    },

};

</script>

<style>
.img-phone{
  padding-left:350px ;
  position: fixed;
  
}

@media only screen and (max-width: 768px) {
  .img-phone{
    left: 0;
    padding-left:70px;
    padding-top: 0;
    position: relative;
    /* position: absolute; */
    /* width: 10px; */
    /* width: 8.33%; */
    
  }
}


</style>