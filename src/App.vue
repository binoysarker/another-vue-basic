<template>
  <div class="">
    <vue-addBlog></vue-addBlog>
    <vue-showBlog></vue-showBlog>
  </div>
</template>

<script>
import AddBlog from './components/AddBlog.vue'
import ShowBlog from './components/showBlog.vue'
export default {
  data () {
    return {

    }
  },
  components: {
    'vue-addBlog':AddBlog,
    'vue-showBlog':ShowBlog,

  },
  methods: {

  },



}
</script>

<style >

</style>
