<template>
  <div class="col-lg-9 wp-list">
    <h3>List Blogs</h3>
    <Table :dataBlogs="dataBlogs" />
  </div>
</template>

<script>
import axios from 'axios'
import Table from './Table.vue'

export default {
  components: { Table },
  name: 'List',

  data() {
    return {
      dataBlogs: [],
    }
  },
  methods: {
    getData() {
      axios.get('http://localhost:4000/blogs').then((res) => {
        this.dataBlogs = res.data
        console.log(this.dataBlogs)
      })
    },
  },
  mounted() {
    this.getData()
  },
}
</script>