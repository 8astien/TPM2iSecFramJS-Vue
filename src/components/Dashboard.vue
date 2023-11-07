<template>
    <div>
      <h1>Dashboard</h1>
      <p>Bienvenue sur votre dashboard, {{ userDetails.firstname }} {{ userDetails.lastname }}</p>
      <form @submit.prevent="submitFeedback">
        <input type="text" v-model="feedback" placeholder="Laissez votre feedback...">
        <button type="submit">Envoyer</button>
      </form>      
      <div v-html="lastFeedback"></div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'UserDashboard',
    data() {
      return {
        feedback: '',
        lastFeedback: '',
        userDetails: JSON.parse(localStorage.getItem('userInfo')) || { firstname: '', lastname: '' },
      };
    },
    methods: {
      submitFeedback() {
        this.lastFeedback = this.feedback;
        this.feedback = '';
      },
    },
  };
  </script>
  