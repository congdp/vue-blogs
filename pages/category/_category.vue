<template>
  <div class="col-lg-9" style="border-left: 1px solid #bdbdbd">
    <list-product-by-category :dataProducts="dataProducts" />
  </div>
</template>

<script>
import axios from 'axios'
import { URL_API } from '../../constants/constants'
import ListProductByCategory from '../../components/Category/ListProductByCategory.vue'
export default {
  components: {
    ListProductByCategory,
  },
  data() {
    return {
      dataProducts: [],
    }
  },
  methods: {
    /**
     * get list blog
     */
    getListPrioductByCategory(id) {
      axios.get(URL_API + 'products/' + id).then((res) => {
        this.dataProducts = res.data.data
        console.log(this.dataProducts)
      })
    },
  },
  mounted() {
    console.log(this.$route.params)
    // this.getData()
    this.getListPrioductByCategory(this.$route.params.category)
  },
}
</script>
