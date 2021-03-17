<template>
  <create-edit :title="title" />
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
