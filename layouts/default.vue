<template>
  <div class="container">
    <div class="header my-3">
      <web-header />
    </div>
    <div class="row">
      <web-menu/>
      <Nuxt />
    </div>
  </div>
</template>
<script>
import WebHeader from '../components/WebHeader'
import WebMenu from '../components/WebMenu'
export default {
  components: {
    WebHeader,
    WebMenu
   
  },
}
</script>
<style>
</style>