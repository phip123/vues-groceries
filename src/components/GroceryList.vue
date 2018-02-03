<template>
  <ul>
    <li
      is="grocery-item"
      v-for="grocery in groceries"
      :key="grocery.id"
      :grocery="grocery"
      @save="save"
      @remove="remove"
      @check="check">
    </li>
  </ul>
</template>

<script>
import GroceryItem from './GroceryItem'

export default {
  components: {GroceryItem},
  name: 'grocery-list',
  props: ['groceries'],
  methods: {
    save (item) {
      this.$emit('update', item)
    },
    remove (item) {
      this.$emit('remove', item)
    },
    check (item) {
      this.$emit('check',item)
    }
  }
}
</script>

<style scoped>

</style>
