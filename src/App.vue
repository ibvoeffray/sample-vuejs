<template>
  <img src="<%= BASE_URL %>print-BBB.PNG" />
  <div id="app">

    <h1>Avant de commencer qui peut me créer un formulaire de contact online en 2 minutes dans cette salle?</h1>
    
  </div>
</template>

<script>
export default {
  data() {
    return {
      form: {
        name: "",
        email: "",
        subject: "",
        message: "",
      },
      errors: {},
    };
  },
  methods: {
    validateEmail(email) {
      const re = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
      return re.test(email);
    },
    submitForm() {
      this.errors = {};

      if (!this.form.name) {
        this.errors.name = "Le nom est requis.";
      }

      if (!this.form.email) {
        this.errors.email = "L'email est requis.";
      } else if (!this.validateEmail(this.form.email)) {
        this.errors.email = "L'email est invalide.";
      }

      if (!this.form.subject) {
        this.errors.subject = "Le sujet est requis.";
      }

      if (!this.form.message) {
        this.errors.message = "Le message est requis.";
      }

      if (Object.keys(this.errors).length === 0) {
        alert("Formulaire soumis avec succès !");
        this.resetForm();
      }
    },
    resetForm() {
      this.form.name = "";
      this.form.email = "";
      this.form.subject = "";
      this.form.message = "";
    },
  },
};
</script>

<style scoped>
#app {
  max-width: 600px;
  margin: 50px auto;
  padding: 20px;
  background-color: #f9f9f9;
  border-radius: 8px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

h1 {
  text-align: center;
  margin-bottom: 20px;
  background-color: #f9f9f9;
}

.form-group {
  margin-bottom: 15px;
}

label {
  font-weight: bold;
  display: block;
  margin-bottom: 5px;
}

input,
textarea {
  width: 100%;
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 4px;
  box-sizing: border-box;
}

textarea {
  resize: vertical;
}

button {
  display: block;
  width: 100%;
  padding: 10px;
  background-color: #007bff;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

button:hover {
  background-color: #0056b3;
}

.error {
  color: red;
  font-size: 14px;
  margin-top: 5px;
}
</style>
