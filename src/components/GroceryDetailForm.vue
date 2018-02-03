<template>
  <div class="card">
    <div class="card-content">
      <div class="field">
        <div class="control is-expanded">
          <input
            v-model="model.name"
            class="input is-medium is-rounded"
            type="text"
            title="Name">
        </div>
      </div>

      <b-field>
        <b-input rounded v-model="model.quantity"
                 type="number"
                 size="is-medium"
                 title="Quantity"></b-input>
        <b-select placeholder="Unit"
                  rounded
                  size="is-medium"
                  v-model="model.unit">
          <option v-for="unit in units" :key="unit" :value="unit">{{unit}}</option>
        </b-select>
      </b-field>
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
import {UNITS} from '../constants'

export default {
  props: ['grocery'],
  name: 'grocery-detail-form',
  data () {
    return {
      model: {
        id: this.grocery.id,
        name: this.grocery.name,
        quantity: this.grocery.quantity || 0,
        unit: this.grocery.unit || 'None'
      },
      units: UNITS
    }
  },
  methods: {
    cancel () {
      this.$emit('cancel')
    },
    save () {
      this.$emit('save', this.model)
    }
  }
}
</script>

<style scoped>

</style>
