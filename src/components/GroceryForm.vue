<template>
  <div class="field">
    <div class="field has-addons">
      <div class="control is-expanded">
        <input
          v-bind:class="{ 'is-danger': error }"
          v-model="model.name"
          class="input is-medium is-rounded"
          type="text"
          placeholder="Anything you want">
      </div>
      <div class="control">
        <button
          @click="add"
          :class="{ 'is-danger': error, 'is-primary': !error }"
          class="button is-medium is-rounded">
          Add
        </button>
      </div>
    </div>
    <p v-if="error"
       class="help is-danger">Please enter something</p>
  </div>

</template>

<script>
export default {
  name: 'grocery-form',
  data () {
    return {
      model: this.emptyModel(),
      error: false
    }
  },
  methods: {
    add () {
      if (!this.model.name || this.model.name.length === 0) {
        this.error = true
        return
      } else {
        this.error = false
      }

      this.$emit('submit', this.model)
      this.model = this.emptyModel()
      console.log(this.model)
    },
    emptyModel () {
      return {
        name: '',
        quantity: 0,
        unit: 'None',
        done: false
      }
    }
  }
}
</script>

<style scoped>

</style>
