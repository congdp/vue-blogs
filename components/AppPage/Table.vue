<template>
  <div>
    <table class="table table-bordered">
      <thead>
        <tr>
          <th scope="col">ID</th>
          <th scope="col">Tin</th>
          <th scope="col">Loại</th>
          <th scope="col">Trạng thái</th>
          <th scope="col">Vị trí</th>
          <th scope="col">Ngày public</th>
          <th scope="col">Edit</th>
          <th scope="col">Delete</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(blog, index) in dataBlogs" :key="index">
          <th scope="row">{{ blog.id }}</th>
          <td>{{ blog.title }}</td>
          <td>
            <div v-for="(cate, index) in CATEGORY" :key="index">
              <p v-if="index == blog.category">{{ cate }}</p>
            </div>
          </td>
          <td>{{ blog.public }}</td>
          <td>{{ filterPosition(blog.position) }}</td>
          <td>{{ blog.data_pubblic }}</td>
          <td>
            <nuxt-link :to="`/blog/${blog.id}`"
              ><button class="btn btn-primary">Edit</button></nuxt-link
            >
          </td>
          <td>
            <button
              class="btn btn-danger"
              @click="deleteBlog(index, blog.id)"
              onclick="return confirm('Bạn có muốn xóa ?')"
            >
              Delete
            </button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>
<script>
import axios from 'axios'
import { DATA_CATE } from '@/constants/constants.js'
import { DATA_POS } from '@/constants/constants.js'
export default {
  name: 'Table',
  data() {
    return {
      CATEGORY: DATA_CATE,
      POSITION: DATA_POS,
    }
  },
  props: {
    dataBlogs: {
      type: Array,
      default: () => [],
    },
    getData: Function,
  },
  methods: {
    /**
     * delete blog
     */
    deleteBlog(index, id) {
      axios.delete('http://localhost:4000/blogs/' + id).then((res) => {
        console.log('xoa thanh cong')
        this.dataBlogs.splice(index, 1)
      })
    },

    /**
     * get name position
     */
     filterPosition(pos) {
      return pos
        .map((item) => {
          return this.POSITION[item];
        })
        .join(",");
    },
  },
}
</script>