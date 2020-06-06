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
        md="4"
      >
        <v-card class="elevation-12">
          <v-toolbar
            color="primary"
            dark
            flat
          >
            <v-toolbar-title>Personal details</v-toolbar-title>
          </v-toolbar>
          <v-card-text>
            <v-form>
              <v-text-field
                label="First Name"
                name="firstName"
                prepend-icon="mdi-account"
                type="text"
                v-model="form.firstName"
              ></v-text-field>
              <v-text-field
                label="Last Name"
                name="lastName"
                prepend-icon="mdi-account"
                type="text"
                v-model="form.lastName"
              ></v-text-field>
              <v-text-field
                label="Email"
                name="email"
                prepend-icon="mdi-email"
                type="email"
                v-model="form.email"
              ></v-text-field>
            </v-form>
          </v-card-text>
          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn
              color="primary" type="submit"
              @click.native.prevent="onSubmit"
              :disabled="!formIsValid"
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
    name: "form-b",
    methods: {
      onSubmit() {
        const baseUrl = process.env.baseUrl;

        if (!this.formIsValid) return;
        axios
          .post(`${baseUrl}/api`, { params: this.form })
          .then(response => {
            console.log('Form has been posted', response);
          }).catch(err => {
            console.log('An error occurred', err);
        });
      }
    },
    computed: {
      formIsValid() {
        return (
          this.form.firstName.length > 0 &&
          this.form.lastName.length > 0 &&
          this.form.email.length > 0
        );
      }
    },
    data: () => ({
        form: {
          firstName: '',
          lastName: '',
          email: ''
        }
    }),
    components: {

    }
  }
</script>
