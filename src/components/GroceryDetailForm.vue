<template>
  <div class="card">
    <div class="card-content">
      <div class="field has-addons">
        <div class="control is-expanded">
          <input
            v-model="model.name"
            class="input is-medium is-rounded"
            type="text"
            title="Name">
        </div>
      </div>
    </div>
    <footer class="card-footer">
      <a
        href="#"
        @click.prevent="cancel"
        class="card-footer-item">Cancel</a>
      <a
        href="#"
        @click.prevent="save"
        class="card-footer-item">Save</a>
    </footer>
  </div>
</template>

<script>
  export default {
    props: ['grocery'],
    name: 'grocery-detail-form',
    data() {
      return {
        model: {
          id: this.grocery.id,
          name: this.grocery.name
        }
      }
    },
    methods: {
      cancel() {
        this.$emit('cancel')
      },
      save() {
        this.$emit('save', this.model)
      }
    }
  }
</script>

<style scoped>

</style>
