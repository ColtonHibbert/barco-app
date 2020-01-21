<template>
    <div>
        <div class="comment-container">
            <div>Comment Name: {{this.comment.name}}</div>
            <div>By User {{this.comment.email}}</div>
            <div class="comment-body">{{this.comment.body}}</div>
        </div>
    </div>
</template>

<script>

export default {
    name: "Comment",
    props: ["comment"],
    data() {
        return {

        }
    },
}
</script>

<style scoped>
    .comment-container {
        background: #9EEBCF;
        margin-top: 10px;
        margin-bottom: 5px;
        border-radius: .25rem;
    }
    .comment-body {
        margin-top: 10px;
    }
</style>