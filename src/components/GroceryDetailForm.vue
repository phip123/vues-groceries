<template>
  <div class="card">
    <div class="card-content">

      <b-field
        :type="nameError? 'is-danger': ''"
        :message="nameError? 'Empty no good' : ''">
        <b-input rounded
                 size="is-medium"
                 v-model.trim="model.name"
        ></b-input>

      </b-field>

      <b-field :type="quantityError? 'is-danger': ' '"
        :message="quantityError? 'Value must be equal or greater than 0' : ' '">
        <b-field :type="quantityError? 'is-danger': ' '">
            <b-input rounded v-model.number="model.quantity"
                     type="number"
                     size="is-medium"
                     title="Quantity"></b-input>

          <b-select
            placeholder="Unit"
            rounded
            size="is-medium"
            v-model="model.unit">
            <option v-for="unit in units" :key="unit" :value="unit">{{unit}}</option>
          </b-select>

        </b-field>
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
import BField from 'buefy/src/components/field/Field'

export default {
  components: {BField},
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
      nameError: false,
      quantityError: false,
      units: UNITS
    }
  },
  methods: {
    cancel () {
      this.$emit('cancel')
    },
    save () {
      this.nameError = !this.model.name || this.model.name.length === 0

      this.quantityError = this.model.quantity < 0

      if (this.nameError || this.quantityError) {
        return
      }
      this.$emit('save', this.model)
    }
  },
  computed: {}
}
</script>

<style scoped>

</style>
