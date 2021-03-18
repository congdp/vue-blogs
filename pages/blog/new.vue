<template>
  <create-edit :title="title" />
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
