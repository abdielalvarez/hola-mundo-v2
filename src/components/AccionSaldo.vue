<template>
  <div>
      <button @click="accion" :disabled="isDisabled">{{texto}}</button>
  </div>
</template>

<script>
export default {
    props: {
        texto: String,
        // isDisabled: Boolean,
        isDisabled: {
            type: Boolean,
            default: false,
        }
    },
    methods: {
        accion() {
            this.$emit('accion')
        }
    },
}
</script>

<style>

</style>