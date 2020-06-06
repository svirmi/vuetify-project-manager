<template>
  <form novalidate>
    <slot
      :group="group"
      :fields="fields"
      :validation="validationBag"
    >
    </slot>
  </form>
</template>

<script>
    export default {
        name: "Wrapper",
      props: {
          group: {
            type: String,
            required: true
          },
          behaviour: {
            type: String,
            required: false
        }
      },
      data() {
          return {
            fileds: {},
            validationBag: {}
          }
      }
    }
</script>

<style scoped>

</style>
