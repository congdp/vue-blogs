<template>
  <div class="col-lg-9">
    <h3>{{ title }}</h3>
    <form class="w-50 mb-5">
      <div class="form-group">
        <label for="title">Tiêu đề</label>
        <input
          type="text"
          class="form-control"
          id="title"
          placeholder="Tiêu đề"
          v-model="form.title"
        />
      </div>
      <div class="form-group">
        <label for="desc">Mô tả</label>
        <input
          type="text"
          class="form-control"
          id="desc"
          placeholder="Mô tả"
          v-model="form.des"
        />
      </div>

      <div class="form-group">
        <label for="detail">Chi tiết</label>
        <textarea
          class="form-control"
          id="detail"
          rows="3"
          v-model="form.detail"
        ></textarea>
      </div>
      <div class="mb-3">
        <label for="thumb">Hình ảnh</label> <br />
        <input type="file" id="thumb" />
      </div>
      <div class="mb-3">
        <label for="type">Loại</label> <br />
        <select name="type" id="type" v-model="form.category">
          <option v-for="(cat, index) in CATEGORY" :key="index" :value="cat.id">
            {{ cat.name }}
          </option>
        </select>
      </div>
      <label for="" class="d-block">Vị trí</label>
      <div class="form-group">
        <!-- <p>Vị trí</p> -->
        <ul class="list-group list-group-flush list-unstyled">
          <li
            v-for="(post, key) in POSITION"
            v-bind:key="post"
            class="list-group-control"
          >
            <div class="custom-control custom-checkbox">
              <input
                type="checkbox"
                :value="key"
                class="custom-control-input"
                :id="'check' + key"
                v-model="form.position"
              />
              <label class="custom-control-label" :for="'check' + key">{{
                post
              }}</label>
            </div>
          </li>
        </ul>
      </div>
      <label for="" class="d-block mt-3">Public</label>
      <div class="form-check">
        <input
          class="form-check-input"
          type="radio"
          v-bind:value="1"
          v-model="form.public"
        />
        <label class="form-check-label d-block" for="exampleRadios1">
          Yes
        </label>
        <input
          class="form-check-input"
          type="radio"
          v-bind:value="2"
          v-model="form.public"
        />
        <label class="form-check-label" for="exampleRadios1"> No </label>
      </div>
      <div class="form-group mt-3">
        <label for="desc">Date Public</label>
        <input
          type="date"
          class="form-control w-50"
          id="desc"
          v-model="form.data_pubblic"
        />
      </div>
      <div class="active d-flex justify-content-center">
        <button
          class="btn btn-success mr-2"
          @click="createBlog"
          v-if="title === 'New Blogs'"
        >
          Submit
        </button>
        <button
          v-if="title === 'Edit Blogs'"
          type="button"
          class="btn btn-success mr-2"
          @click="updateBlog(form.id)"
        >
          Edit
        </button>
        <button class="btn btn-primary">Clear</button>
      </div>
    </form>
  </div>
</template>

<script>
import axios from 'axios'
const CATEGORY = [
  { id: 1, name: 'thời sự' },
  { id: 2, name: 'thế giới' },
  { id: 3, name: 'kinh doanh' },
  { id: 4, name: 'giải trí' },
  { id: 5, name: 'thời sự' },
  { id: 6, name: 'thế giới' },
  { id: 7, name: 'kinh doanh' },
  { id: 8, name: 'giải trí' },
  { id: 9, name: 'thời sự' },
]
const POSITION = ['Việt Nam', 'Châu Á', 'Châu Âu', 'Châu Mỹ']
export default {
  props: ['title'],
  name: 'New',
  data() {
    return {
      CATEGORY,
      POSITION,
      form: {
        id: '',
        title: '',
        des: '',
        detail: '',
        category: '',
        public: '',
        data_pubblic: '',
        position: [],
        thumbs: '',
      },
    }
  },
  methods: {
    createBlog() {
      axios.post('http://localhost:4000/blogs', this.form).then((res) => {
        alert('thêm thành công')
      })
      this.$router.push('/blog/list')
    },
    getBlogByID(id) {
      axios
        .get('http://localhost:4000/blogs/' + id)
        .then((res) => (this.form = res.data))
    },
    updateBlog(id) {
      axios.put('http://localhost:4000/blogs/' + id, this.form).then((res) => {
        // alert('thêm thành công')
      })
      this.$router.push('/blog/list')
    },
  },
  mounted() {
      this.getBlogByID(this.$route.params.id)
  },
}
</script>