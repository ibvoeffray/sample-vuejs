<template>
  <div class="container">
    <h1>Contactez-nous</h1>
    <form @submit.prevent="sendEmail">
      <div>
        <label for="name">Nom</label>
        <input v-model="form.name" type="text" id="name" required>
      </div>
      <div>
        <label for="email">Email</label>
        <input v-model="form.email" type="email" id="email" required>
      </div>
      <div>
        <label for="message">Message</label>
        <textarea v-model="form.message" id="message" required></textarea>
      </div>
      <button type="submit">Envoyer</button>
    </form>
    <div id="status">{{ statusMessage }}</div>
  </div>
</template>

<script>

export default {
  data() {
    return {
      form: {
        name: '',
        email: '',
        message: ''
      },
      statusMessage: ''
    };
  },
 
};
</script>

<style scoped>
body {
  font-family: Arial, sans-serif;
  background-color: #f4f4f4;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  margin: 0;
}

.container {
  background-color: white;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

h1 {
  text-align: center;
}

label {
  display: block;
  margin-top: 10px;
}

input, textarea {
  width: 100%;
  padding: 10px;
  margin-top: 5px;
  border: 1px solid #ccc;
  border-radius: 4px;
}

button {
  width: 100%;
  padding: 10px;
  background-color: #5cb85c;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  margin-top: 15px;
}

button:hover {
  background-color: #4cae4c;
}

#status {
  margin-top: 15px;
  text-align: center;
}
</style>
