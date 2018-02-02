<template>
  <ul>
    <li
      is="grocery-item"
      v-for="grocery in groceries"
      :grocery="grocery"
      @save="save">
    </li>
  </ul>
</template>

<script>
  import GroceryItem from './GroceryItem';

  export default {
    components: {GroceryItem},
    name: "grocery-list",
    props: ['groceries'],
    methods: {
      save(item) {
        this.$emit('update', item);
      }
    }
  }
</script>

<style scoped>

</style>
