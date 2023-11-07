<template>
  <div>
    <h1>Commentaires</h1>
    <form @submit.prevent="submitComment">
      <textarea v-model="newComment" placeholder="Laissez un commentaire..."></textarea>
      <button type="submit">Publier</button>
    </form>
    
    <div class="comments" v-for="comment in comments" :key="comment.id">
      <div v-html="comment.content"></div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      newComment: '',
      comments: []
    };
  },
  created() {
    this.fetchComments();
  },
  methods: {
    async fetchComments() {
      try {
        const response = await axios.get('http://localhost:3000/comments');
        this.comments = response.data;
      } catch (error) {
        console.error("Il y a eu une erreur lors de la récupération des commentaires :", error);
      }
    },
    async submitComment() {
      try {
        const response = await axios.post('http://localhost:3000/comments', {
          content: this.newComment
        });
        this.comments.push(response.data);
        this.newComment = '';
      } catch (error) {
        console.error("Il y a eu une erreur lors de l'envoi du commentaire :", error);
      }
    }
  }
};
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

  .comments {
    text-align: left;
    width: 400px;
    margin: 0 auto;
  }

  .comments div {
    margin: 1rem 0;
  }
  </style>