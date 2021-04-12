<template>
  <div class="col-lg-9" style="border-left: 1px solid #bdbdbd">
    <product-detail :dataProducts="dataProducts" />
  </div>
</template>

<script>
import axios from 'axios'
import { URL_API } from '../../constants/constants'
import ProductDetail from '../../components/Products/ProductDetail.vue'
export default {
  components: {
    ProductDetail,
  },
  data() {
    return {
      dataProducts: [],
    }
  },
  methods: {
    /**
     * get product detail
     */
    getProductDetail(id) {
      axios.get(URL_API + 'product/' + id).then((res) => {
        this.dataProducts = res.data.data
        console.log(this.dataProducts)
      })
    },
  },
  mounted() {
    console.log(this.$route.params)
    // this.getData()
    this.getProductDetail(this.$route.params.id)
  },
}
</script>
