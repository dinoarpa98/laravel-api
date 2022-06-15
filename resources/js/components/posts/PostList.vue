<template>
    <div class="container">
      <h1 class="text-center text-danger">PostList</h1> 
    </div>
</template>

<script>
import axios from 'axios';

export default{
    name: "PostList",
    methods:{
        getPosts(){
            axios.get("http://127.0.0.1:8000/api/posts")
            .then((res) => {
              console.log(res.data)
            })
        }
    },

    mounted(){
        this.getPosts();
    }
}
</script>

<style scoped>

</style>