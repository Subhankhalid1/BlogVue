<template>
  <div id="app">
  <!-- <h1>Root Component</h1> -->
  <app-header></app-header>
  <Add-Blog></Add-Blog>
  <show-blogs></show-blogs>
  <!-- <router-view></router-view> -->
  </div>
</template>

<script>
  import addBlog from './components/addBlog.vue'
  import showBlogs from './components/showBlogs.vue'
  import Header from './components/header.vue'
export default {
components:{
  "Add-Blog":addBlog,
  "show-blogs":showBlogs,
  "app-header":Header
},

  data () {
    return {
     
    }
  }
}
</script>

<style>
/* #app{
  display: flex;
  justify-items: center;
  justify-content: center;
  border: 3px solid greenyellow;
} */
</style>
