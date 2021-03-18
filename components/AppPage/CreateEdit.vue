<template>
  <div class="col-lg-9">
    <h3>{{ title }}</h3>
    <ul v-if="errors.length > 0" class="alert alert-danger">
      <li v-for="error in errors" v-bind:key="error">{{ error }}</li>
    </ul>
    <div class="w-50 mb-5">
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
          <option v-for="(cat, index) in CATEGORY" :key="index" :value="index">
            {{ cat }}
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
          v-bind:value="true"
          v-model="form.public"
        />
        <label class="form-check-label d-block" for="exampleRadios1">
          Yes
        </label>
        <input
          class="form-check-input"
          type="radio"
          v-bind:value="false"
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
          @click="createBlog()"
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
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import { DATA_CATE } from '@/constants/constants.js'
import { DATA_POS } from '@/constants/constants.js'
export default {
  props: ['title'],
  name: 'New',
  data() {
    return {
      CATEGORY :DATA_CATE,
      POSITION:DATA_POS,
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
      errors: [],
    }
  },
  methods: {
    /**
     * create blog
     */
    createBlog() {
      this.validate()
      if (this.errors.length > 0) {
        return this.errors
      } else {
        axios.post('http://localhost:4000/blogs', this.form).then((res) => {
          alert('them thanh cong')
        })
        this.$router.push('/blog')
      }
    },

    /**
     * get blog by id
     */
    getBlogByID(id) {
      axios
        .get('http://localhost:4000/blogs/' + id)
        .then((res) => (this.form = res.data))
    },

    /**
     * update blog
     */
    updateBlog(id) {
      this.validate()
      if (this.errors.length > 0) {
        return this.errors
      } else {
        axios
          .put('http://localhost:4000/blogs/' + id, this.form)
          .then((res) => {
            alert(' Sửa thành công')
          })
        this.$router.push('/blog')
      }
    },

    /**
     * check validate
     */
    validate() {
      this.errors = []
      if (this.form.title == '') {
        this.errors.push('title không được trống')
      }
      if (this.form.des == '') {
        this.errors.push('des không được trống')
      }
      if (this.form.detail == '') {
        this.errors.push('deatil không được trống')
      }
      if (this.form.category == '') {
        this.errors.push('category không được trống')
      }
      if (this.form.position == []) {
        this.errors.push('position không được trống!')
      }
    },
  },
  mounted() {
    if (this.$route.params.id != null) {
      this.getBlogByID(this.$route.params.id)
    }
  },
}
</script>