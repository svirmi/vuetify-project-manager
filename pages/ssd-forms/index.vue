<template>
  <v-container
    class="fill-height"
    fluid
  >
    <v-row
      align="center"
      justify="center"
    >
      <v-col
        cols="12"
        sm="8"
        md="8"
      >
        <v-card class="elevation-12">
          <v-toolbar
            color="primary"
            dark
            flat
          >
            <v-toolbar-title>Form #1</v-toolbar-title>
          </v-toolbar>
          <v-card-text>
            <v-form v-model="isValid">
              <v-text-field
                label="First Name"
                name="firstName"
                prepend-icon="mdi-account"
                type="text"
                counter
                v-model="form.firstName"
                :rules="firstNameRules"
              ></v-text-field>
              <v-text-field
                label="Email"
                v-model="form.email"
                :rules="emailRules"
                error-count="2"
                required
              ></v-text-field>
              <v-text-field
                label="Password"
                v-model="form.password"
                type="password"
                :rules="passwordRules"
                error-count="5"
                required
              ></v-text-field>
            </v-form>
          </v-card-text>
          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn
              color="primary" type="submit"
              @click.native.prevent="onSubmit"
              :disabled="!isValid"
            >Go!</v-btn>
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
  import axios from 'axios';
  export default {
    name: "ssd-form-1",
    methods: {
      onSubmit() {
        const baseUrl = process.env.baseUrl;

        if (!this.isValid) return;

        axios
          .post(`${baseUrl}/api`, { params: this.form })
          .then(response => {
            console.log('Form has been posted', response);
          }).catch(err => {
            console.log('An error occurred', err);
        });
      },
    },
    computed: {},
    data() {
      return {
        form: {
          firstName: null,
          email: null,
          password: null,
        },
        isValid: true,
        firstNameRules: [
          v => !!v || 'First name is required',
          v => (v && v.length >= 3) || 'First name must have 3+ characters'
        ],
        emailRules: [
          v => !!v || 'Email is required',
          v => /.+@.+/.test(v) || 'E-mail must be valid'
        ],
        passwordRules: [
          v => !!v || 'Password is required',
          v => (v && v.length >= 5) || 'Password must have 5+ characters',
          v => /(?=.*[A-Z])/.test(v) || 'Must have one uppercase character',
          v => /(?=.*\d)/.test(v) || 'Must have one number',
          v => /([!@$%])/.test(v) || 'Must have one special character [!@#$%]'
        ]
      }
    },
    components: {

    }
  }
</script>
