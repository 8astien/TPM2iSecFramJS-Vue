<template>
  <div>
    <h1>Changer de photo de profil</h1>
    <input type="file" @change="uploadFile">
    <!-- Intentionnellement vulnérable: affichage du contenu du fichier -->
    <div v-html="fileContent"></div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      fileContent: ''
    };
  },
  methods: {
    uploadFile(event) {
      const file = event.target.files[0];
      if (file) {
        const reader = new FileReader();
        reader.onload = (e) => {
          // Directly setting the content of the file as HTML
          this.fileContent = e.target.result;
        };
        reader.readAsText(file);
      }
    }
  }
};
</script>
