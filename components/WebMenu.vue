<template>
  <div class="col-lg-3 h-100 menu">
    <li class="list-unstyled">
      <nuxt-link to="/product"
        ><a href="" class="text-center d-block">Home</a></nuxt-link
      >
    </li>
    <ul class="list-group list-unstyled" >
      <li v-for="(item, index) in dataCategory" :key="index">
        <nuxt-link :to="`/category/${item.id}`"
          ><a href="" class="text-center d-block">{{item.name}}</a></nuxt-link
        >
      </li>
     
    </ul>
    <li class="list-unstyled">
      <nuxt-link to="/product"
        ><a href="" class="text-center d-block">About Us</a></nuxt-link
      >
    </li>
    <li class="list-unstyled">
      <nuxt-link to="/product"
        ><a href="" class="text-center d-block">Contact</a></nuxt-link
      >
    </li>
  </div>
</template>

<script>
import { URL_API } from '../constants/constants'
import axios from 'axios'
export default {
  name: 'WebMenu',
  data() {
    return {
      dataCategory: [],
    }
  },
  methods: {
    /**
     * get list blog
     */
    getListCategory() {
      axios.get( URL_API + 'category').then((res) => {
        this.dataCategory = res.data.data
        // this.$emit('getData',this.dataBlogs)
        console.log(this.dataCategory)
      })
    },
  },
  mounted() {
    this.getListCategory()
  },
}
</script>
<style>
 a {
  color: #000;
  font-size: 16px;
  font-weight: 500;
  text-transform: uppercase;
  display: block;
  margin-bottom: 10px;
  padding: 3px 0px;
  /* border-bottom:1px solid #dbdbdb ; */
  
}
col-lg-9 li {
  /* padding: 10px  */
}
</style>