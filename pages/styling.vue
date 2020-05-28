<template>
<div class="styling">

  <h1>Some CSS classes examples</h1>

  <p class="headline text-capitalize">Lorem ipsum dolor sit amet, consectetur adipisicing elit. Aliquam eaque eos itaque necessitatibus obcaecati officia quaerat repellat, similique soluta sunt totam vero voluptas voluptatibus! Accusantium adipisci amet ex placeat quam?</p>
  <p class="pink lighten-4 orange--text text--darken-4">Lorem ipsum dolor sit amet, consectetur adipisicing elit. Ad at blanditiis delectus eum fuga, fugit illum iste magnam maiores maxime minima omnis optio porro possimus quod sapiente, tempora velit veniam.</p>

  <v-btn class="pink black--text">Click Me</v-btn>
  <v-btn depressed color="pink">Click Me Again</v-btn>
  <v-btn color="pink">Click Me Again</v-btn>

  <v-btn color="pink">
    <v-icon medium>mdi-home</v-icon>
  </v-btn>

  <v-btn color="pink">
    <v-icon dark left>mdi-home</v-icon>Home
  </v-btn>

</div>
</template>

<script>
    export default {
        name: "styling"
    }
</script>

<style scoped>

</style>
