<template>
  <div>
    <slot
      :group="group"
      :fields="fields"
      :validation="validationBag"
    ></slot>
  </div>
</template>

<script>
    export default {
      name: "Wrapper",
      props: {
          group: {
            type: String,
            required: false
          },
          behaviour: {
            type: String,
            required: false
        }
      },
      data: () => ({
        fields: {},
        validationBag: {}
      }),
    }
</script>
