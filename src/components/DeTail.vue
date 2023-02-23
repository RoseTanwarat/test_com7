<template>
  <div class="container">
    <h3>ซื้อ iPhone 12</h3>

    <section >
        <h5>รุ่น</h5>
        <div class="model" v-for="item in items" :key='item.index' >
            <div :class="[selected.name === item.name ? isActive:undefined,boxZone]" @click="selectProduct(item)"  >
          <div class="box1" >{{ item.name }}</div>
          <div class="box2">ราคาเริ่มต้น {{ item.price }}</div>
        </div>
        <!-- <div class="box-zone">
          <div class="box1">Phone 12 Pro Max</div>
          <div class="box2">ราคาเริ่มต้น ฿32,800</div>
        </div> -->
        </div>
      </section>

    <selection class="img">
        <img class="imgChange" id='imgChange'>
    </selection>

    <section class="color">
      <h5>สี</h5>
      <br />
       <div class="color" v-for="color in colors" :key='color.col' >
            <div :class="[select.circle === color.col ? isActive:undefined,'box-zone-color']" @click="selectColor(color)"  >
                <div :class="[`circle` ,`circle-${color.circle}`]"></div>
                <div class="box3">{{ color.col }}</div>
            </div>
        </div>
      <!-- <div class="box-zone-color" @click="changeImage('https://store.storeimages.cdn-apple.com/8756/as-images.apple.com/is/iphone-13-pink-select-2021?wid=470&hei=556&fmt=png-alpha&.v=1629842709000')"  >
        <div class="circle circle-1"></div>
        <div class="box3">ชมพู</div>
      </div>
      <div class="box-zone-color" @click="changeImage('https://store.storeimages.cdn-apple.com/8756/as-images.apple.com/is/iphone-13-starlight-select-2021?wid=470&hei=556&fmt=png-alpha&.v=1629907845000')">
        <div class="circle circle-2"></div>
        <div class="box3">เงิน</div>
      </div>
      <div class="box-zone-color" @click="changeImage('https://store.storeimages.cdn-apple.com/8756/as-images.apple.com/is/iphone-13-midnight-select-2021?wid=470&hei=556&fmt=png-alpha&.v=1629907844000')">
        <div class="circle circle-3"></div>
        <div class="box3">มิดไนท์</div>
      </div>
      <div class="box-zone-color" @click="changeImage('https://store.storeimages.cdn-apple.com/8756/as-images.apple.com/is/iphone-13-blue-select-2021?wid=470&hei=556&fmt=png-alpha&.v=1629842712000')">
        <div class="circle circle-4"></div>
        <div class="box3">น้ำเงิน</div>
      </div> -->
    </section>

    <section class="color">
      <h5>ขนาด</h5>
      <br />
      <div class="model" v-for="size in sizes" :key='size.index' >
            <div :class="[selectSize.name === size.name ? isActive:undefined,'box-zone-color']" @click="selectedSize(size)"  >
          <div class="box4" >{{ size.name }}</div>
          <div class="box5">ราคาเริ่มต้น {{ size.price }}</div>
        </div>
        </div>

      <!-- <div class="box-zone-color">
        <div class="box4">64GB</div>
        <div class="box5">฿28,800.00</div>
      </div>
      <div class="box-zone-color">
        <div class="box4">128GB</div>
        <div class="box5">฿32,800.00</div>
      </div>
      <div class="box-zone-color">
        <div class="box4">512GB</div>
        <div class="box5">฿36,800.00</div>
      </div>
      <div class="box-zone-color">
        <div class="box4">1TB</div>
        <div class="box5">฿39,800.00</div>
      </div> -->
    </section>

    <section class="model">
      <div class="text-buy">คุณต้องการรับสินค้าด้วยวิธีใด</div>

      <div class="model" v-for="pickUp in pickUps" :key='pickUp.index' >
            <div :class="[selectpickUp.name === pickUp.name ? isActive:undefined,'box-zone-buy']" @click="selectHowToPickUp(pickUp)"  >
                <div class="icon"> <img :src="pickUp.icon"/> </div>
                <div class="box6" >{{ pickUp.name }}</div>
        <br />

                <div class="box7">{{ pickUp.price }}</div>
           </div>
    </div>

      <!-- <div class="box-zone-buy">
        <div class="icon"><img src="@/assets/At_Store.png" /></div>
        <div class="box6">บริการรับสินค้าหน้าร้าน</div>
        <br />
        <div class="box7">จองเริ่มต้นเพียง ฿3,000.00 เท่านั้น</div>
      </div>

      <div class="box-zone-buy">
        <div class="icon"><img src="@/assets/Delivery.png" /></div>
        <div class="box6">บริการจัดส่งถึงบ้าน</div>
        <br />
        <div class="box7">ชำระสินค้าในราคาเต็ม</div>
      </div> -->
      <div class="line"><hr /></div>
    </section>

    <div class="btn">
      <button class="checkout" @click="() => TogglePopup('buttonTriger')">
        ยืนยันการสั่งซื้อล่วงหน้า
      </button>
    </div>
    <PopUp
      v-if="popupTriger.buttonTriger"
      :TogglePopUp="() => TogglePopup('buttonTriger')"
    ></PopUp>

    <footer class="footer">
      <div class="text-footer-left">
        Copyright © Interview. All rights reserved.
      </div>
      <div class="icon-footer-right"><img src="@/assets/Brands.png" /></div>
    </footer>
  </div>
</template>

<script>
import { ref } from "vue";
import PopUp from "./PopUp.vue";
// import IPhone from "./IPhone.vue";
import store from "../assets/At_Store.png"
import delivery from "../assets/Delivery.png"
export default {
  name: "DeTail",
  data() {
    return { 
        items:[{name:"iphone 12",price:'฿32,800'},{name:"iphone 11",price:'฿28,000'}],
        selected:{name:""},
        isClick: false ,
        boxZone:"box-zone",
        isActive:"active",

        colors:[{circle:'1',col:'ชมพู',img:"https://store.storeimages.cdn-apple.com/8756/as-images.apple.com/is/iphone-13-pink-select-2021?wid=470&hei=556&fmt=png-alpha&.v=1629842709000"},{circle:'2',col:'เงิน',img:"https://store.storeimages.cdn-apple.com/8756/as-images.apple.com/is/iphone-13-starlight-select-2021?wid=470&hei=556&fmt=png-alpha&.v=1629907845000"},{circle:'3',col:'มิดไนท์',img:"https://store.storeimages.cdn-apple.com/8756/as-images.apple.com/is/iphone-13-midnight-select-2021?wid=470&hei=556&fmt=png-alpha&.v=1629907844000"},{circle:'4',col:'น้ำเงิน',img:"https://store.storeimages.cdn-apple.com/8756/as-images.apple.com/is/iphone-13-blue-select-2021?wid=470&hei=556&fmt=png-alpha&.v=1629842712000"}],
        select:{circle:""},
        boxZoneColor:"box-zone-color",

        sizes:[{name:'64GB',price:'฿28,800.00'},{name:'128GB',price:'฿32,800.00'},{name:'512GB',price:'฿36,800.00'},{name:'1TB',price:'฿39,800.00'}],
        selectSize:{name:""},
        boxZoneSize:"box-zone-color",

        pickUps:[{icon:store,name:'บริการรับสินค้าหน้าร้าน',price:'จองเริ่มต้นเพียง ฿3,000.00 เท่านั้น'},{icon:delivery,name:'บริการจัดส่งถึงบ้าน',price:'ชำระสินค้าในราคาเต็ม'}],
        selectpickUp:{name:""},
        boxZoneBuy:"box-zone-buy",
    };
  },
  components: { 
    PopUp ,

},
  setup() {
    const popupTriger = ref({
      buttonTriger: false,
    });
    const TogglePopup = (trigger) => {
      popupTriger.value[trigger] = !popupTriger.value[trigger];
    };
    return {
      popupTriger,
      PopUp,
      TogglePopup,
    
    };
  },
  methods: {
    selectProduct(item){
        console.log(item.name)
        this.selected={name:item.name}

    },
     selectColor(color){
        console.log(color.col)
        this.select={circle:color.col}
        let img = document.querySelector('.imgChange');
        img.setAttribute('src',color.img)

    },
    selectedSize(size){
        console.log(size.name)
        this.selectSize={name:size.name}
    },
    selectHowToPickUp(pickUp){
        console.log(pickUp.name)
        this.selectpickUp={name:pickUp.name}
        // let img = document.querySelector('.icon');
        // img.setAttribute('src',pickUp.img)
    },
    changeImage(fileName){
       let img = document.querySelector('.imgChange');
       img.setAttribute('src',fileName)
    },
    borderChange(event) {
      this.isClick = !this.isClick;
      this.isClicked = !this.isClicked;
      
      event.currentTarget.classList.remove('non-active');
      event.currentTarget.classList.add('active');
    },
  },
  mounted(){
    let img = document.getElementById('imgChange').value;
    if(img == null || img ==''){
        document.getElementById('imgChange').src='https://store.storeimages.cdn-apple.com/8756/as-images.apple.com/is/iphone-13-pink-select-2021?wid=470&hei=556&fmt=png-alpha&.v=1629842709000'
    }
  }
};
</script>

<style>
.active{
    border-color: #5bba47 !important;
}

h3 {
  text-align: right;
  padding-right: 430px;
  padding-bottom: 50px;
  padding-top: 50px;
  font-weight: 700 !important;
  font-size: 40px !important;
}

h5 {
  text-align: right;
  padding-right: 640px;
  font-weight: 700 !important;
  font-size: 24px;
  
}

.text-buy {
  padding-left: 18px;
  font-weight: 700;
  font-size: 22px !important;
}

.model {
  display: grid;
  /* grid-template-rows: repeat(2,1fr); */
  float: right;
  width: 680px;
  margin-bottom: 20px;
}

.box-zone {
  display: grid;
  grid-template-columns: repeat(2, 300px);
  /* //ความห่างข้อความด้านใน */
  padding: 30px;
  width: 500px;
  /* //ขนาดbox */
  margin: 0 20px 20px 20px;
  background-color: #fff;
  border-radius: 10px;
  border: 1px solid #bbb;
}

.box-zone:hover {
  cursor: pointer;
}

/* .box-zone:active{
    border:1px solid #5bba47;
} */

.box1 {
  font-weight: bolder;
}

.color {
  /* padding-right: 500px; */
  display: grid;
  padding-left: 10px;
  float: right;
  width: 670px;
  grid-template-columns: repeat(2, 260px);
  margin-bottom: 30px;
}

.box-zone-color {
  width: 240px;
  height: 110px;
  margin: 10px;
  margin-left: 0;
  background-color: #fff;
  border-radius: 10px;
  border: 1px solid #bbb;
}

.box-zone-color:hover {
  cursor: pointer;
}

.circle {
  margin-left: 100px;
  margin-top: 20px;
  margin-bottom: 10px;
  width: 30px;
  height: 30px;
  
  /* border: solid 5px darkcyan; */
  border-radius: 100%;
}

.circle-1{
    /* background-image: url('@/assets/Image4.png'); */
    background-color: rgb(246, 202, 202);
}

.circle-2{
    background-image: url('@/assets/Image5.png');
}

.circle-3{
    background-image: url('@/assets/Image6.png');
}

.circle-4{
    background-color: rgb(95, 124, 197);
}

.box3 {
  display: flex;
  justify-content: center;
  align-items: center;
}

.box4 {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-top: 20px;
  margin-bottom: 10px;
  font-weight: bolder;
}

.box5 {
  display: flex;
  justify-content: center;
  align-items: center;
  color: #808080;
}

.box-zone-buy {
  display: grid;
  grid-template-columns: 80px 1fr;
  background-color: #fff;
  border-radius: 10px;
  border: 1px solid #bbb;
  padding: 20px;
  /* padding-bottom: 0%; */
  width: 500px;
  margin: 20px;
}

.box-zone-buy:hover {
  cursor: pointer;
}

.box6 {
  font-weight: 600;
  font-size: 20px;
  line-height: 32px;
  display: flex;
  align-items: last baseline;
  padding-top: 10px;
}

.box7 {
  color: #808080;
  font-weight: 400;
  font-size: 16px;
  line-height: 25px;
}

.icon {
  width: auto;
  height: 35px;
  padding-left: 10px;
  padding-bottom: 0;
  padding-top: 10px;
}

hr {
  width: 500px;
}

.line {
  padding-left: 20px;
  padding-top: 10px;
  padding-bottom: 10px;
  margin-bottom: 0%;
  /* padding-bottom: 0%; */
}
.checkout {
  color: #fff;
  padding: 15px;
  padding-left: 170px;
  padding-right: 170px;
  background-color: #5bba47;
  border-color: #5bba47;
  border-radius: 10px;
}

.btn {
  /* display: grid; */
  float: right;
  width: 822px;
  margin-bottom: 50px;
  padding: 0 !important;
  /* border: none; */
  border: 0;
    border-width: 0;
}

.text-footer-left {
  font-size: 15px;
  color: #808080;
  position: absolute;
  left: 180px;
  top: 1800px;
  padding-bottom: 20px;
}

.icon-footer-right {
  position: absolute;
  right: 480px;
  top: 1800px;
}

.img{
  /* padding-left:350px ; */
  top: 20px;
  position: fixed;
}

@media only screen and (max-width: 768px) {
    h3{
        text-align: center;
        padding-right: 0;
    }
    .icon-footer-right{
        display: none;
    }
    .text-footer-left{
        display:none;
    }
    .img{
    position: relative;
    left: 300px;
    justify-content: center;
    display: flex;
    margin-top: 50px;
  }
  .model{
    margin-bottom: 0;
  }
}

</style>
