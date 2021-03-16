<template>
  <div class="col-lg-9" >
    <h3>List Blogs</h3>
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
      <th scope="row">{{blog.id}}</th>
      <td>{{blog.title}}</td>
      <td>{{blog.category}}</td>
      <td>{{blog.public}}</td>
       <td>{{blog.position}}</td>
      <td>{{blog.data_pubblic}}</td>
      <td><a href="" class="btn btn-primary">Edit</a></td>
          <td><a href="" class="btn btn-danger">Delete</a></td>

    </tr>
    
  </tbody>
</table>
  </div>
</template>

<script>
import axios from "axios"

export default {
 
  name: 'List',
  data (){
    return {
      dataBlogs :[],
    }
  },
  methods:{
    getData(){
      axios.get("http://localhost:3001/blogs").then(
        (res)=>{
          this.dataBlogs=res.data
          console.log(this.dataBlogs)
        })
   
    }
  },
  mounted(){
    this.getData()
  }
}
</script>