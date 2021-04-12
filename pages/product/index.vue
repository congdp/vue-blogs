<template>
  <div class="col-lg-9" style="border-left: 1px solid #bdbdbd">
    <list-product :dataProducts="dataProducts" />
  </div>
</template>

<script>
import axios from 'axios'
import { URL_API } from '../../constants/constants'
import ListProduct from '../../components/Products/ListProduct.vue'
export default {
  components: {
    ListProduct,
  },
  data() {
    return {
      dataProducts: [],
    }
  },
  methods: {
    /**
     * get list product
     */
    getData() {
      axios.get(URL_API + 'product').then((res) => {
        this.dataProducts = res.data.data
        console.log(this.dataProducts)
      })
    },
  },
  mounted() {
    this.getData()
  },
}
</script>
