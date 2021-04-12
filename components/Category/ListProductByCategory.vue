<template>
  <div>
    <h3>List Product</h3>
    <div class="item-list">
      <ul class="card-group row list-unstyled">
        <li
          class="col-md-4 mb-4"
          v-for="(item, index) in dataProducts"
          :key="index"
        >
          <nuxt-link :to="`/product/${item.id}`">
            <a href="">
              <div class="article-item">
                <div class="card">
                  <img
                    v-bind:src="'http://localhost:8000/' + item.thumb"
                    class="img-fluid"
                    alt="..."
                  />
                  <div class="card-body item-detail">
                    <p class="card-title item-title mb-0 pb-3">
                      {{ item.name }}
                    </p>
                    <div class="d-flex" style="justify-content: space-between">
                      <span class="price text-danger">
                        {{ formatFinalPrice(item.price, item.discount) }}
                      </span>
                      <span
                        class="price text-muted"
                        style="text-decoration: line-through; font-size: 13px"
                      >
                        {{ formatOriginalPrice(item.price) }}
                      </span>
                    </div>
                  </div>
                </div>
              </div>
            </a>
          </nuxt-link>
        </li>
      </ul>
    </div>
  </div>
</template>
<script>
import axios from 'axios'
import swal from 'sweetalert2'
export default {
  name: 'ListProductByCategory',
  props: {
    dataProducts: {
      type: Array,
      default: () => [],
    },
  },
  data() {
    return {
      dataCategory: [],
    }
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

    getListCate(id) {
      axios.get('http://localhost:8000/api/products/' + id).then((res) => {
        this.dataProducts = res.data.data
        console.log(this.dataProducts)
      })
    },
  },
}
</script>
