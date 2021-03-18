<template>
  <div class="col-lg-9">
    <h3>Search Blog</h3>
    <div action="" class="mb-3">
      <div class="form-group row">
        <label for="title" class="col-sm-2 col-form-label">Tiêu đề</label>
        <div class="col-sm-10">
          <input type="text" class="form-control" v-model="search" id="title" />
        </div>
      </div>
      <button class="btn btn-success" @click="searchBlog()">Search</button>
    </div>
    <Table :dataBlogs="listBlog" />
  </div>
</template>
<script>
import axios from 'axios'
import Table from './Table.vue'
export default {
  name: 'Search',
  data() {
    return {
      listBlog: [],
      search: '',
    }
  },
  components: {
    Table,
  },
  methods: {
    /**
     * search blog
     */
    searchBlog() {
      axios
        .get('http://localhost:4000/blogs' + '?title_like=' + this.search)
        .then((res) => {
          this.listBlog = res.data
          console.log(res.data)
        })
    },
  },
}
</script>
<style>
.wp-list {
  max-width: 100%;
  padding-left: 0px;
}
</style>