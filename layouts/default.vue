<template>
  <div class="container">
    <div class="header my-3">
      <app-header />

    </div>
    <div class="row ">
      <app-menu/>
       <Nuxt/>
    </div>
   
  </div>
</template>
<script>
import AppHeader from '../components/AppHeader.vue'
import AppMenu from '../components/AppMenu.vue'
// import List from '../components/AppPage/List.vue'
export default {
  components: {
    AppHeader,
    AppMenu,
    // AppP,
  },
}
</script>
<style>
</style>