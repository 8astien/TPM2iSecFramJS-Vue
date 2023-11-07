<template>
  <LoginForm msg="Login Form"/>
  <Dashboard />
  <UserProfile />
  <CommentsSection/>
</template>

<script>

import LoginForm from './components/LoginForm.vue';
import Dashboard from './components/Dashboard.vue';
import UserProfile from './components/UserProfile.vue';
import CommentsSection from './components/CommentsSection.vue'

export default {
  name: 'App',
  components: {
    LoginForm,
    Dashboard,
    UserProfile,
    CommentsSection
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
