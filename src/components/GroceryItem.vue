<template>
  <div style="margin-bottom: 20px">
    <grocery-item-detail
      v-if="!showEdit"
      :grocery="grocery"
      @check="check"
      @edit="edit"
      @remove="remove">

    </grocery-item-detail>
    <grocery-detail-form
      v-if="showEdit"
      :grocery="grocery"
      @save="save"
      @cancel="cancel"
    >
    </grocery-detail-form>
  </div>

</template>

<script>
// TODO wennn "Got it!" Hinten einreihen und ausgrauen. nur delete button offen lassen
import GroceryForm from './GroceryForm'
import GroceryItemDetail from './GroceryItemDetail'
import GroceryDetailForm from './GroceryDetailForm'

export default {
  data () {
    return {
      showEdit: false
    }
  },
  components: {
    GroceryDetailForm,
    GroceryItemDetail,
    GroceryForm
  },
  name: 'grocery-item',
  props: ['grocery'],
  methods: {
    save (item) {
      console.log('save: ' + item.name)
      this.$emit('save', item)
    },
    cancel () {
      console.log('cancel')
      this.showEdit = !this.showEdit
    },
    check () {
      console.log('check')
    },

    edit () {
      console.log('edit')
      this.showEdit = !this.showEdit
    },

    remove () {
      console.log('remove')
    }
  }
}
</script>

<style scoped>

</style>
