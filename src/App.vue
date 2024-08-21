<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Formulaire de Contact - Vue.js</title>
    <script src="https://cdn.jsdelivr.net/npm/vue@2"></script>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4;
            margin: 0;
            padding: 20px;
        }
        .contact-form {
            background-color: #fff;
            padding: 20px;
            border-radius: 8px;
            max-width: 500px;
            margin: 0 auto;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
        }
        .contact-form h2 {
            margin-bottom: 20px;
        }
        .contact-form label {
            display: block;
            margin-bottom: 8px;
        }
        .contact-form input, 
        .contact-form textarea {
            width: 100%;
            padding: 10px;
            margin-bottom: 20px;
            border: 1px solid #ccc;
            border-radius: 4px;
        }
        .contact-form button {
            padding: 10px 20px;
            background-color: #007bff;
            color: #fff;
            border: none;
            border-radius: 4px;
            cursor: pointer;
        }
        .contact-form button:hover {
            background-color: #0056b3;
        }
        .error {
            color: red;
            font-size: 14px;
            margin-bottom: 10px;
        }
    </style>
</head>
<body>

    <div id="app" class="contact-form">
        <h2>Contactez-nous</h2>
        <form @submit.prevent="submitForm">
            <div>
                <label for="name">Nom</label>
                <input type="text" id="name" v-model="name" placeholder="Votre nom">
                <div class="error" v-if="errors.name">{{ errors.name }}</div>
            </div>
            <div>
                <label for="email">Email</label>
                <input type="email" id="email" v-model="email" placeholder="Votre email">
                <div class="error" v-if="errors.email">{{ errors.email }}</div>
            </div>
            <div>
                <label for="subject">Sujet</label>
                <input type="text" id="subject" v-model="subject" placeholder="Sujet">
                <div class="error" v-if="errors.subject">{{ errors.subject }}</div>
            </div>
            <div>
                <label for="message">Message</label>
                <textarea id="message" v-model="message" placeholder="Votre message" rows="5"></textarea>
                <div class="error" v-if="errors.message">{{ errors.message }}</div>
            </div>
            <button type="submit">Envoyer</button>
        </form>
    </div>

    <script>
        new Vue({
            el: '#app',
            data: {
                name: '',
                email: '',
                subject: '',
                message: '',
                errors: {}
            },
            methods: {
                validateEmail(email) {
                    const re = /^[a-zA-Z0-9._-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/;
                    return re.test(email);
                },
                submitForm() {
                    this.errors = {};

                    if (!this.name) {
                        this.errors.name = 'Veuillez entrer votre nom.';
                    }

                    if (!this.email) {
                        this.errors.email = 'Veuillez entrer votre email.';
                    } else if (!this.validateEmail(this.email)) {
                        this.errors.email = 'Veuillez entrer un email valide.';
                    }

                    if (!this.subject) {
                        this.errors.subject = 'Veuillez entrer un sujet.';
                    }

                    if (!this.message) {
                        this.errors.message = 'Veuillez entrer un message.';
                    }

                    if (Object.keys(this.errors).length === 0) {
                        alert('Merci pour votre message ! Nous vous contacterons bientôt.');
                        this.resetForm();
                    }
                },
                resetForm() {
                    this.name = '';
                    this.email = '';
                    this.subject = '';
                    this.message = '';
                }
            }
        });
    </script>

</body>
</html>

