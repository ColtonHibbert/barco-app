<template>
    <div>
        <div>Comments</div>
        <div 
            v-for="comment in commentList" v-bind:key="comment.id">
            <Comment 
                v-bind:comment="comment"
            />
        </div>
    </div>
</template>

<script>
import Comment from './Comment';

export default {
    name: "Comments",
    components: {
        Comment
    },
    props: { postId: Number },
    data() {
        return {
            commentList: []
        }
    },
    created() {
        fetch(`https://jsonplaceholder.typicode.com/comments?postId=${this.postId}`) 
        .then(res => res.json())
        .then(comments => this.commentList = comments)
        .catch(err => {
            /* eslint-disable no-console */
            console.log(err)
            /* eslint-enable no-console */
        })
    }   
}
</script>

<style scoped>
    
</style>