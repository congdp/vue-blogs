<template>
  <!-- <div> -->
  <!-- <app-header/> -->
  <create-edit :title="title" />
  <!-- </div> -->
</template>

<script>
import CreateEdit from '../../components/AppPage/CreateEdit'
export default {
  data() {
    return {
      title: 'Edit Blogs',
    }
  },
  components: {
    CreateEdit,
  },
}
</script>
