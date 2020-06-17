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
            <v-form>
              <v-text-field
                label="First Name"
                name="firstName"
                prepend-icon="mdi-account"
                type="text"
                counter
                v-model="form.firstName"
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
      },
    },
    computed: {
      formIsValid() {
        return (
          this.form.firstName.length > 0
        );
      }
    },
    data() {

      return {
        form: {
          firstName: '',
        },
      }
    },
    components: {

    }
  }
</script>
