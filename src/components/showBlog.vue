<template>
  <div id='show-blogs' v-theme:column='"narrow"'>
    <h1>All Blog Posts</h1>
    <div class="single-blog" v-for="blog in blogs" :key="blog.key">
      <h3 v-rainbow>{{blog.title | to-uppercase}}</h3>
      <p>{{blog.body | to-short}}</p>
    </div>
  </div>
</template>
<script>
export default {
  data: () => ({
    blogs:[],
  }),
  created() {
    //do something after creating vue instance
    this.$http.get('https://jsonplaceholder.typicode.com/posts')
    .then((data) =>
        this.blogs = data.body.slice(0,10),

      )
  }
}
</script>
<style scoped>
#show-blogs{
  max-width: 800px;
  margin: 0 auto;
}
.single-blog{
  padding: 20px;
  margin: 20px 0;
  box-sizing: border-box;
  background: #eee;
}
</style>
