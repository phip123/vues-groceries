<template>
  <div class="field has-addons">
    <div class="control is-expanded">
      <input
        v-model="model.name"
        class="input is-medium is-rounded"
        type="text"
        placeholder="Anything you want">
    </div>
    <div class="control">
      <button
        @click="add"
        class="button is-primary is-medium is-rounded">
        Add
      </button>
    </div>
  </div>
</template>

<script>
    export default {
        name: "grocery-form",
      data () {
        return {
          model: {
            name: ''
          }
        }
      },
      methods: {
          add() {

            this.$emit('submit',this.model)
          }
      }
    }
</script>

<style scoped>

</style>
