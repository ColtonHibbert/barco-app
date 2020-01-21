<template>
    <div>
        <div 
            class="users-home-page"
            v-on:click="$emit('users-page-false', true)"
        >Click here for Users Page</div>
        <h1 class="top-spacing">Posts Page for {{selectedUser.name}}</h1>
        <h2>You can check out my awesome posts below</h2>
        <div 
            v-for="post in userPosts" 
            v-bind:key="post.id"
        >
            <Post 
                v-bind:post="post"
            />
        </div>     
    </div>
</template>

<script>
import Post from './Post';

export default {
    name: "Posts",
    components: {
        Post,
    },
    props: {
        usersPage: Boolean,
        selectedUser: Object
    },
    data() {
        return {
             userPosts: []
        }
    },
    methods: {

    }, 
    created() {
        fetch(`https://jsonplaceholder.typicode.com/posts?userId=${this.selectedUser.id}`) 
        .then(res => res.json())
        .then(posts => this.userPosts = posts)
        .catch(err => {
            /* eslint-disable no-console */
            console.log(err)
            /* eslint-enable no-console */
        })
    }
}
</script>

<style scoped>
    .users-home-page {
        float: left;
        background: #9EEBCF;
        border-radius: .25rem;
        padding: 2px;
    }
</style>