<template>
    <div id="add-blog">
    <h1>Add New Blog Post</h1>
    <form v-if="!submitted">
        <label>Title: </label>
        <input type="text" v-model.lazy="blog.title" required/>
        <label>Description: </label>
        <textarea v-model.lazy="blog.content"></textarea>
        <div id="checkBoxes">
            <label>Walk</label>
            <input type="checkbox" value="walk" v-model="blog.categories"/>
            <label>Car</label>
            <input type="checkbox" value="car" v-model="blog.categories"/>
            <label>Bike</label>
            <input type="checkbox" value="bike" v-model="blog.categories"/>
        </div>
        <p>Author:</p>
        <select v-model="blog.author">
            <option v-for="author in authors">{{ author }}</option>
           
        </select>
        <button v-on:click.prevent="post">Add Blog</button>
    </form>
    <div v-if="submitted">
        <h3>Thanks for adding a blog. </h3>
    </div>
    <div id="preview">
        <h3>Preview BLogs</h3>
        <p>Blog Title: {{ blog.title }}</p>
        <p>Blog Description:</p>
        <p>{{ blog.content }}</p>
        <p>Blog Categories: </p>
        <ul>
            <li v-for="category in blog.categories">{{ category }}</li>
        </ul>
        <p>Author: {{ blog.author }}</p>

    </div>
    </div>
  </template>
  
  <script>
  export default {
  
    data () {
      return {
      blog:{
        title:"",
       content:"",
       categories:[],
       author:""
      },
      authors:["1st Author","2nd Author","3rd Author"],
      submitted:false
      }
    },
    methods:{
        post:function(){
            this.$http.post("https://jsonplaceholder.typicode.com/posts",{
                title:this.blog.title,
                body:this.blog.content,
                userId:101
            }).then(function(data){
                console.log(data);
                this.submitted=true
            })
        }
    }
  }
  </script>
  
  <style>
 #add-blog *{
    box-sizing: border-box;
}
#add-blog{
    margin: 20px auto;
    max-width: 500px;
}
label{
    display: block;
    margin: 20px 0 10px;
}
input[type="text"], textarea{
    display: block;
    width: 100%;
    padding: 8px;
}
#preview{
    padding: 10px 20px;
    border: 1px dotted #ccc;
    margin: 30px 0;
}
h3{
    margin-top: 10px;
}
#checkBoxes input{
    display:inline-block;
    margin-right: 10px;

}
#checkBoxes label{
    display: inline-block;
}
  </style>
  

