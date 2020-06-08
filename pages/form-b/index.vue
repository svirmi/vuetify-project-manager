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
            <v-toolbar-title>Personal details</v-toolbar-title>
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
              <v-text-field
                label="Last Name"
                name="lastName"
                prepend-icon="mdi-account"
                type="text"
                counter
                v-model="form.lastName"
              ></v-text-field>
              <v-text-field
                label="Email"
                name="email"
                prepend-icon="mdi-email"
                type="email"
                v-model="form.email"
              ></v-text-field>

              <v-autocomplete
                v-model="friends"
                :disabled="isUpdating"
                :items="people"
                filled
                color="blue-grey lighten-2"
                label="Select"
                item-text="name"
                item-value="name"
              >
                <template v-slot:selection="data">
                  {{ data.item.name }}
                </template>
                <template v-slot:item="data">
                  <template v-if="typeof data.item !== 'object'">
                    <v-list-item-content v-text="data.item"></v-list-item-content>
                  </template>
                  <template v-else>
                    <v-list-item-content>
                      <v-list-item-title v-html="data.item.name"></v-list-item-title>
                      <v-list-item-subtitle v-html="data.item.group"></v-list-item-subtitle>
                    </v-list-item-content>
                  </template>
                </template>
              </v-autocomplete>

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
      remove (item) {
        const index = this.friends.indexOf(item.name)
        if (index >= 0) this.friends.splice(index, 1)
      },
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
    data() {

      const srcs = {
        1: 'https://cdn.vuetifyjs.com/images/lists/1.jpg',
        2: 'https://cdn.vuetifyjs.com/images/lists/2.jpg',
        3: 'https://cdn.vuetifyjs.com/images/lists/3.jpg',
        4: 'https://cdn.vuetifyjs.com/images/lists/4.jpg',
        5: 'https://cdn.vuetifyjs.com/images/lists/5.jpg'
      }


      return {
        form: {
          firstName: '',
          lastName: '',
          email: ''
        },
        autoUpdate: true,
        friends: ['Sandra Adams', 'Britta Holt'],
        isUpdating: false,
        name: 'Midnight Crew',
        people: [
          { header: 'Group 1' },
          { name: 'Sandra Adams', group: 'Group 1', avatar: srcs[1] },
          { name: 'Ali Connors', group: 'Group 1', avatar: srcs[2] },
          { name: 'Trevor Hansen', group: 'Group 1', avatar: srcs[3] },
          { name: 'Tucker Smith', group: 'Group 1', avatar: srcs[2] },
          { divider: true },
          { header: 'Group 2' },
          { name: 'Britta Holt', group: 'Group 2', avatar: srcs[4] },
          { name: 'Jane Smith ', group: 'Group 2', avatar: srcs[5] },
          { name: 'John Smith', group: 'Group 2', avatar: srcs[1] },
          { name: 'Sandra Williams', group: 'Group 2', avatar: srcs[3] },
        ],
        title: 'The summer breeze',
      }
    },
    watch: {
      isUpdating (val) {
        if (val) {
          setTimeout(() => (this.isUpdating = false), 3000)
        }
      },
    },
    components: {

    }
  }
</script>
