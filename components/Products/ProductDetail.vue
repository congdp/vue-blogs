<template>
  <div>
    <div id="content" class="fl-right">
      <div class="section" id="info-product-wp">
        <div class="section-detail row">
          <div class="thumb col-md-5">
            <img
              v-bind:src="'http://localhost:8000/' + dataProducts.thumb"
              alt=""
              class="img-fluid"
            />
          </div>
          <div class="detail col-md-7">
            <h3 class="title">{{ dataProducts.name }}</h3>
            <p class="price pr-4">
              {{ formatFinalPrice(dataProducts.price, dataProducts.discount) }}
              <span class="text-muted" style="text-decoration: line-through; font-size: 17px"> {{  formatOriginalPrice(dataProducts.price) }} </span>
            </p>
            <div class="desc-short">
              <h5>Mô tả sản phẩm:</h5>
              <p>{{ dataProducts.des }}</p>
            </div>
            <div class="num-order-wp">
              <span>Số lượng:</span>
              <input type="text" id="num-order" name="num-order" value="1" />
              <a href="" title="" class="add-to-cart"
                >Thêm giỏ hàng</a
              >
            </div>
          </div>
        </div>
      </div>
      <div class="section" id="desc-wp">
        <div class="section-head">
          <h3 class="section-title">Chi tiết sản phẩm</h3>
        </div>
        <div class="section-detail">
          <p>
            Lorem Ipsum is simply dummy text of the printing and typesetting
            industry. Lorem Ipsum has been the industry's standard dummy text
            ever since the 1500s, when an unknown printer took a galley of type
            and scrambled it to make a type specimen book. It has survived not
            only five centuries, but also the leap into electronic typesetting,
            remaining essentially unchanged. It was popularised in the 1960s
            with the release of Letraset sheets containing Lorem Ipsum passages,
            and more recently with desktop publishing software like Aldus
            PageMaker including versions of Lorem Ipsum.
          </p>
          <p>
            Lorem Ipsum is simply dummy text of the printing and typesetting
            industry. Lorem Ipsum has been the industry's standard dummy text
            ever since the 1500s, when an unknown printer took a galley of type
            and scrambled it to make a type specimen book. It has survived not
            only five centuries, but also the leap into electronic typesetting,
            remaining essentially unchanged. It was popularised in the 1960s
            with the release of Letraset sheets containing Lorem Ipsum passages,
            and more recently with desktop publishing software like Aldus
            PageMaker including versions of Lorem Ipsum.
          </p>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import axios from 'axios'
export default {
  name: 'ProductDetail',
  props: {
    dataProducts: {
      type: Array,
      default: () => [],
    },
  },
  data() {
    return {}
  },
  methods: {
    formatOriginalPrice(number) {
      return new Intl.NumberFormat('de-DE', {
        style: 'currency',
        currency: 'VND',
      }).format(number)
    },

    formatFinalPrice(price, discount) {
      var number = price - (price * discount) / 100
      console.log(this.number)
      return new Intl.NumberFormat('de-DE', {
        style: 'currency',
        currency: 'VND',
      }).format(number)
    },
  },
}
</script>
<style>
#info-product-wp {
  padding-top: 30px;
}
#info-product-wp .thumb {
  width: 35%;
}
#info-product-wp .detail {
  width: 65%;
  padding-left: 30px;
}
#info-product-wp .detail .title {
  display: block;
  font-family: 'Roboto Medium';
  font-weight: normal;
  font-size: 21px;
  text-transform: uppercase;
  padding-bottom: 10px;
  margin-bottom: 20px;
  border-bottom: 1px solid #bfbfbf;
}
#info-product-wp .detail .price {
  font-size: 24px;
  font-family: 'Roboto Medium';
  font-weight: normal;
  color: #b50000;
  padding-bottom: 10px;
  line-height: 21px;
}
.product-code {
  color: #555;
  margin-bottom: 15px;
}
.product-code span,
.desc-short h5 {
  font-family: 'Roboto Medium';
  font-weight: normal;
  color: #444;
  line-height: 21px;
}
.desc-short p {
  color: #555;
  text-align: justify;
  margin: 10px 0px 20px 0px;
  display: -webkit-box;
  -webkit-line-clamp: 3;
  -moz-line-clamp: 3;
  -o-line-clamp: 3;
  -webkit-box-orient: vertical;
  -moz-box-orient: vertical;
  -o-box-orient: vertical;
  max-height: 100%;
  overflow: hidden;
  line-height: 21px;
}
.num-order-wp {
  padding-bottom: 20px;
}
.num-order-wp span {
  color: #555;
}
.num-order-wp #num-order {
  width: 35px;
  height: 35px;
  line-height: 35px;
  text-align: center;
  border: 1px solid #bbb;
  color: #444;
  border-radius: 3px;
  font-size: 15px;
}
.add-to-cart {
  display: inline-block;
  padding: 7px 15px;
  background: #3a9800;
  color: #fff !important;
  font-size: 13px;
  margin-left: 15px;
  border-radius: 3px;
}
.add-to-cart:hover {
  background: #318000;
}
#desc-wp .section-title {
  padding-bottom: 10px;
}
#desc-wp .section-detail p {
  text-align: justify;
  padding-bottom: 10px;
  color: #444;
}
</style>
