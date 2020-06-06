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
            <v-spacer></v-spacer>
            <v-tooltip bottom>
              <template v-slot:activator="{ on }">
                <v-btn
                  icon
                  large
                  target="_blank"
                  v-on="on"
                >
                  <v-icon>mdi-account</v-icon>
                </v-btn>
              </template>
              <span>Person</span>
            </v-tooltip>
          </v-toolbar>
          <v-card-text>
            <v-form>
              <Wrapper group="update-form">
                <v-text-field
                  slot-scope="props"
                  label="First Name"
                  name="first_name"
                  prepend-icon="mdi-account"
                  type="text"
                  v-model="props.fields.first_name"
                ></v-text-field>
              </Wrapper>
            </v-form>
          </v-card-text>
          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn color="primary">Go!</v-btn>
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
  import Wrapper from "../../components/forms/Wrapper";

  export default {
    name: "form-a",
    data: () => ({

    }),
    components: {
      Wrapper
    }
  }
</script>
