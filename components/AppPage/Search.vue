<template>
  <div class="col-lg-9">
    <h3>Search Blog</h3>
    <form action="">
      <div class="form-group row">
        <label for="title" class="col-sm-2 col-form-label"
          >Tiêu đề</label
        >
        <div class="col-sm-10">
          <input type="text" class="form-control" id="title" />
        </div>
      </div>
     <button class="btn btn-success">Search</button>
    </form>
  </div>
</template>
<script>
export default {
  name: 'Search',
}
</script>