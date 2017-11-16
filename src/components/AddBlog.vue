<template>
  <div class="" id='add-blog'>
    <h1>Add a Blog</h1>
    <div class="" v-if="submited">
      <h3>Data is posted Successfuly</h3>
    </div>
    <form action="" v-if="!submited">
      <label for="">Blog Title:</label>
      <input type="text" v-model.lazy='blog.title' name="" value="" placaholder='Title' require>
      <label for="">Blog Content:</label>
      <textarea name="" v-model.lazy='blog.content' rows="8" cols="20"></textarea>
      <div id="checkboxes">
        <label for="">Ninjas1</label>
        <input type="checkbox" name="" value="ninja1" v-model='blog.categories'>
        <label for="">Ninjas2</label>
        <input type="checkbox" name="" value="ninja2" v-model='blog.categories'>
        <label for="">Ninjas3</label>
        <input type="checkbox" name="" value="ninja3" v-model='blog.categories'>
        <label for="">Ninjas4</label>
        <input type="checkbox" name="" value="ninja4" v-model='blog.categories'>
      </div>
      <label for="">Author</label>
      <select name="" id="" v-model='blog.author'>
        <option :value="author" v-for="author in authors" :key="author.key">{{author}}</option>
      </select>
      <br>
      <br>
      <button type="submit" @click.prevent='SendData' name="button">Add Post</button>
    </form>
    <div id="preview">
      <h3>Preview Blog:</h3>
      <p>Blog Title: {{blog.title}}</p>
      <p>Blog Content:</p>
      <p>{{blog.content}}</p>
      <p>Blog Categories:</p>
      <p>Author</p>
      <p>{{blog.author}}</p>
      <p>category:</p>
      <ul>
        <li v-for="category in blog.categories" :key="category.key">{{category}}</li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      blog:{
        title:'',
        content:'',
        categories:[],
        author:'',
      },
      authors:['author1','author2','author3','author4'],
      submited:false,
    }
  },
  components: {


  },
  methods: {
    SendData(){
      this.$http.post('https://jsonplaceholder.typicode.com/posts',{
        title:this.blog.title,
        body:this.blog.content,
        userId:1,
      }).then(
        (data)=>
              console.log(data),
              this.submited = true)
    }
  },



}
</script>

<style scoped="">
#add-blog *{
  box-sizing: border-box;
  background-color: lightgray;
}
#add-blog{
  margin: 20px auto;
  max-width: 500px;
}
label{
  display: block;
  margin:20px auto;
}
#checkboxes input{
  display: inline-block;
  margin-right: 10px;
}
#checkboxes label{
  display: inline-block;

}


</style>
