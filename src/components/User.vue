<template>
    <div class="user-container">
        <div class="user-info">
            <div >
            {{user.name}} 
            </div>
            <button v-on:click="$emit('send-selected-user', user )">Click here for Posts</button>
        </div>
    </div>
</template>

<script>
    export default {
        name: "User",
        props: ["user"],
    }
</script>

<style scoped>
    .user-info {
        background: #96CCFF;
        padding: 5px;
        border-radius: .25rem;

    }
    .user-container {
        padding: 10px;
        width: 50%;
    }
</style>