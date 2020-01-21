<template>
    <div>
        <h1>Barco-App</h1>
        <h2>List of Users</h2>
        <div v-for="user in users" v-bind:key="user.id">
          <User v-bind:user="user" v-on:send-selected-user="$emit('send-selected-user', user)" />
        </div>
    </div>
</template>

<script>
import User from './User';

export default {
    name: "Users",
    components: {
        User
    },
    props: ["users"]
}
</script>

<style scoped>

</style>