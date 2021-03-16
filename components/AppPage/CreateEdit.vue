<template>
  <div class="col-lg-9">
    <h3>{{title }}</h3>
    <form class="w-50 mb-5">
      <div class="form-group">
        <label for="title">Tiêu đề</label>
        <input
          type="text"
          class="form-control"
          id="title"
          placeholder="Tiêu đề"
        />
      </div>
      <div class="form-group">
        <label for="desc">Mô tả</label>
        <input type="text" class="form-control" id="desc" placeholder="Mô tả" />
      </div>

      <div class="form-group">
        <label for="detail">Chi tiết</label>
        <textarea class="form-control" id="detail" rows="3"></textarea>
      </div>
      <div class="mb-3">
        <label for="thumb">Hình ảnh</label> <br />
        <input type="file" id="thumb" />
      </div>
      <div class="mb-3">
        <label for="type">Loại</label> <br />
        <select name="type" id="type">
          <option value="">--Chọn--</option>
          <option value="">Thời sự</option>
        </select>
      </div>
      <label for="" class="d-block ">Vị trí</label>
      <div class="form-check">
        <input type="checkbox" class="form-check-input" id="exampleCheck1" />
        <label class="form-check-label d-block" for="exampleCheck1"
          >Việt Nam</label
        >
        <input type="checkbox" class="form-check-input" id="exampleCheck1" />
        <label class="form-check-label d-block" for="exampleCheck1"
          >Châu Âu</label
        >
        <input type="checkbox" class="form-check-input" id="exampleCheck1" />
        <label class="form-check-label d-block" for="exampleCheck1"
          >Châu Á</label
        >
        <input type="checkbox" class="form-check-input" id="exampleCheck1" />
        <label class="form-check-label" for="exampleCheck1">Châu Mỹ</label>
      </div>
        <label for="" class="d-block mt-3">Public</label>
      <div class="form-check ">
        <input
          class="form-check-input"
          type="radio"
          name="exampleRadios"
          id="exampleRadios1"
          value="option1"
        />
        <label class="form-check-label d-block" for="exampleRadios1">
          Yes
        </label>
        <input
          class="form-check-input"
          type="radio"
          name="exampleRadios"
          id="exampleRadios1"
          value="option1"
        />
        <label class="form-check-label" for="exampleRadios1"> No </label>
      </div>
      <div class="form-group mt-3">
        <label for="desc">Date Public</label>
        <input type="date" class="form-control w-50" id="desc" />
      </div>
      <div class="active d-flex justify-content-center">
        <button class="btn btn-success mr-2">Submit</button>
        <button class="btn btn-primary">Clear</button>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  props: ["title"],
  name: 'New',
}
</script>