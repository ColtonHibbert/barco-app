<template>
    <div>
        <div class="post-container">
            <h3>{{this.post.title}}</h3>
            <p>{{this.post.body}}</p>
            <button v-on:click="updateShowComments">Click to see or hide my comments</button>
            <Comments 
                v-if="showComments"
                v-bind:postId="post.id"
            />
        </div>
    </div>
</template>

<script>
import Comments from './Comments';

export default {
    name: "Post",
    components: {
        Comments
    },
    props: ["post"],
    data() {
        return {
            showComments: false,
        }
    },
    methods: {
        updateShowComments() {
            this.showComments = !this.showComments
        }
    }
}
</script>

<style scoped>
    .post-container {
        background: #CDECFF;
        margin-top: 20px;
        margin-bottom: 20px;
        border-radius: .25rem;
    }
</style>