<template>
  <div id="app">
   <Users 
    v-if="usersPage" 
    v-bind:users="users" 
    v-bind:selectedUser="selectedUser" 
    v-on:send-selected-user="updateSelectedUser"
   />
   <Posts 
    v-if="usersPage === false"
    v-bind:selectedUser="selectedUser"
    v-on:users-page-false="updatePageToUsers"
   />
  </div>
</template>

<script>
import Users from './components/Users';
import Posts from './components/Posts';

// pass up user from the click,  <Posts />
// then listener method for the user being passed up
// trigger usersPage to be false
// rerender the posts page
// under posts page can list all comments if button is clicked, 
// or hide comments
export default {
  name: 'app',
  components: {
    Users,
    Posts
  },
  data() {
    return {
      usersPage: true,
      users: [],
      selectedUser: {name: 'selectedUser1'}
    }
  },
  methods: {
    updateSelectedUser(user) {
       /* eslint-disable no-console */
      console.log('selected user before', this.selectedUser)
      /* eslint-enable no-console */

      this.selectedUser = user;

       /* eslint-disable no-console */
      console.log('selected user after', this.selectedUser)
      /* eslint-enable no-console */

      this.updatePageToUserPosts();
    },
    updatePageToUserPosts() {
      this.usersPage = false;
    },
    updatePageToUsers() {
      this.usersPage = true 
    }
  },
  created() {
    fetch('https://jsonplaceholder.typicode.com/users')
    .then(res => res.json())
    .then(data => {
      this.users = data
    })
    .catch(err => {
      /* eslint-disable no-console */
      console.log(err)
      /* eslint-enable no-console */
    })
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
