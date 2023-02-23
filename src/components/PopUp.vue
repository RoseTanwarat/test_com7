<template>
  <div class="popUp" >
    <div class="popUp-inner">
      <div class="icon-popup"><img src="@/assets/Order_Success.png" /></div>

      <div class="text-popup">
        <h2>การสั่งซื้อล่วงหน้าสำเร็จ</h2>
        <p>
          การชำระเงินของคุณสำเร็จแล้ว! <br />
          ตอนนี้เราจะส่งอีเมลยืนยันคำสั่งซื้อสำเร็จให้คุณ
        </p>
      </div>

      <div class="btn-popup">
        <button class="popup" @click="TogglePopUp()">ยืนยัน</button>
      </div>
    </div>
  </div>
</template>
<script>

export default {
  name: "PopUp",
  props:['TogglePopUp']
    
  }
</script>

<style lang="scss" scoped>
.popUp {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  z-index: 99;
  background-color: rgba(0, 0, 0, 0.2);

 display: inline-grid;
  // grid-template-rows: 100px 100px 100px;
  //grid-gap: 100px;  
  // display: flex;
  justify-items: center;
  align-items: center;
  text-align: center;

  .popUp-inner {
    background-color: #fff;
    padding: 50px;
    padding-left: 200px;
    padding-right: 200px;
     border-radius: 5px;
  }
}

.popup{
    color: #fff;
  padding: 10px;
  padding-left: 20px;
  padding-right: 20px;
  background-color: #5bba47;
  border-color: #5bba47;
  border-radius: 10px;
}
 .icon-popup{
    padding-bottom: 30px;
 }

 .text-popup{
    padding-bottom: 50px;
 }

 .text-popup > h2{
    padding-bottom: 30px;
 }
</style>
