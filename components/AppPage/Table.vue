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
        <tr v-for="blog in dataBlogs" :key="blog.id">
          <th scope="row">{{ blog.id }}</th>
          <td>{{ blog.title }}</td>
          <td>{{ blog.category }}</td>
          <td>{{ blog.public }}</td>
          <td>{{ blog.position }}</td>
          <td>{{ blog.data_pubblic }}</td>
          <td>
            <nuxt-link :to="`/blog/${blog.id}`"
              ><button class="btn btn-primary">Edit</button></nuxt-link
            >
          </td>
          <td>
            <button
              class="btn btn-danger"
              @click="deleteBlog(blog.id)"
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
export default {
  name: 'Table',
  props: {
    dataBlogs: {
      type: Array,
      default: () => [],
    },
  },
  methods: {
    deleteBlog(id) {
      axios.delete("http://localhost:4000/blogs/" + id).then((res) => {
        console.log("xoa thanh cong");
        axios.get("http://localhost:4000/blogs").then((res) => {
          this.dataBlogs = res.data;
        });
      });
    },
  },
}
</script>