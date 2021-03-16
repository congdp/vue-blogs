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
      title: 'New Blogs',
    }
  },
  components: {
    CreateEdit,
  },
}
</script>
