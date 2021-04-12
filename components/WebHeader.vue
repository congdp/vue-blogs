<template>
  <!-- <div class="row">
      <div class="col-lg-3">
        <img
          alt=""
          class="float-left"
          style="width: 70px"
          src="https://digidinos.com/assets/images/logo.png"
        />
        </div>
      <div class="col-lg-9">
      <h2>Blogs Management</h2>
      </div>
  </div> -->
  <div id="container">
  <div id="header-wp" class="">
    <!-- <div class="wp-inner"> -->
    <div class="row" style="justify-content: space-between; padding: 0px 15px">
      <a href="?page=home" title="" id="logo" class=""
        >DIGIDINOS STORE</a
      >
      <!-- <div id="btn-respon" class="fl-right"><i class="fa fa-bars" aria-hidden="true"></i></div> -->
      <div id="cart-wp" class="">
        <a href="?page=cart" title="" id="btn-cart">
          <span id="icon"
            ><img :src="require(`@/assets/images/icon-cart.png`)" alt=""
          /></span>
          <span id="num">5</span>
        </a>
      </div>
    </div>

    </div>
  </div>
  <!-- </div> -->
</template>

<script>
export default {
  name: 'WebHeader',
}
</script>
<style>
#header-wp {
  border-bottom: 1px solid #bdbdbd;
}
#logo {
  display: block;
  font-family: 'Roboto Bold';
  text-transform: uppercase;
  font-size: 21px;
  color: #333;
  padding: 20px 0px;
}
 /* #btn-cart{ position: relative;} */
#btn-cart{ 
    position: relative;
    display: block;
    padding: 15px 0px;
}
#btn-cart #num{
    position: absolute;
    top: 5px;
    right: -8px;
    color: #b70000;
    font-family: 'Roboto Medium';
} 
</style>