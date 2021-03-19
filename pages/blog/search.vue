<template>
  <div class="col-lg-9">
    <search @getKeyWord="searchBlog" />
    <list-blogs :dataBlogs="dataBlogs" @getListBlogs="searchAfterDelete" />
  </div>
</template>

<script>
import axios from 'axios'
import ListBlogs from '../../components/Blogs/ListBlogs.vue'
import Search from '../../components/Blogs/Search'
export default {
  components: {
    Search,
    ListBlogs,
  },
  data() {
    return {
      dataBlogs: [],
      keySearch: '',
    }
  },
  methods: {
    /**
     * search blog by key search
     */
    searchBlog(data) {
      this.keySearch = data
      axios
        .get('http://localhost:4000/blogs' + '?title_like=' + data)
        .then((res) => {
          this.dataBlogs = res.data
          console.log(res.data)
        })
    },
    /**
     * reload list blog after delete
     */
    searchAfterDelete() {
      this.searchBlog(this.keySearch)
    },
  },
}
</script>
