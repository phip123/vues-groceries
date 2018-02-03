<template>
  <div style="margin-bottom: 20px">
    <transition name="item">
      <grocery-item-detail
        v-if="!showEdit"
        :grocery="grocery"
        @check="check"
        @edit="edit"
        @remove="remove">

      </grocery-item-detail>
      <grocery-detail-form
        key="form"
        v-if="showEdit"
        :grocery="grocery"
        @save="save"
        @cancel="cancel"
      >
      </grocery-detail-form>
    </transition>
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
  props: {
    grocery: {
      type: Object,
      default: function () {
        return {
          id: -1,
          name: '',
          quantity: 0,
          unit: 'None',
          done: false
        }
      }
    }
  },
  methods: {
    save (item) {
      console.log('save: ' + item.name)
      this.showEdit = !this.showEdit
      this.$emit('save', item)
    },
    cancel () {
      console.log('cancel')
      this.showEdit = !this.showEdit
    },
    check () {
      console.log('check')
      this.$emit('check', this.grocery)
    },

    edit () {
      console.log('edit')
      this.showEdit = !this.showEdit
    },

    remove () {
      console.log('remove')
      this.$emit('remove', this.grocery)
    }
  }
}
</script>

<style scoped>
.item-enter-active {
  animation: bounce-in .3s;

}
.item-leave-active {
}
@keyframes bounce-in {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}
</style>
