<template>
    <div class="container">

        <Loader v-if="isLoading"/>

        <ul v-if="posts.length">
            <li class="d-flex" v-for="post in posts" :key="post.id">
                {{post.title}}
            </li>
        </ul>
        <h1 v-else class="mx-3">Non ci sono post</h1>
    </div>
</template>

<script>
    import axios from 'axios';
    import Loader from '../Loader.vue';

    export default {
        name: "PostsList",

        components: {

            Loader
        },

        data() {
            return {
                posts: [],
                isLoading: true
            }
        },

        methods: {
            getPosts() {
                axios.get("http://127.0.0.1:8000/api/posts")
                    .then((res) => {
                        // console.log(res.data.post)
                        this.posts = res.data.posts;
                    }).then(()=> {
                        console.log('arrays');
                        this.isLoading=false;
                    })
            }
        },

        mounted() {
            this.getPosts();
        }
    }

</script>

<style scoped>

</style>
