<template>
  <div class="login__form">
    <h1>Création de compte</h1>
    <form @submit.prevent="submitForm">
      <input v-model="email" type="email" placeholder="Email" />
      <input v-model="firstname" type="text" placeholder="First Name" />
      <input v-model="lastname" type="text" placeholder="Last Name" />
      <input v-model="password" type="password" placeholder="Password" />
      <button type="submit">Login</button>
    </form>
  </div>
</template>

<script>
export default {
  name: 'LoginForm',
  data() {
    return {
      email: '',
      firstname: '',
      lastname: '',
      password: '',
    };
  },
  methods: {
    submitForm() {
      // Simulation d'un appel API pour se connecter
      const fakeApiResponse = {
        data: {
          token: 'fake-jwt-token'
        }
      };
      
      localStorage.setItem('sessionToken', fakeApiResponse.data.token);
      localStorage.setItem('userInfo', JSON.stringify({
        email: this.email,
        firstname: this.firstname,
        lastname: this.lastname
      }));      
      alert('Création de compte réussie');
    }
  }
}
</script>

  
  <style scoped>
  form {
    display: flex;
    flex-direction: column;
    width: 200px;
    align-items: center;
    justify-content: center;
    margin: 0 auto;
  }
  input {
    margin: 1rem;
  }
  </style>
  