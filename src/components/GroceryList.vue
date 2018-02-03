<template>
  <transition-group name="list" tag="ul" mode="in-out">
    <li
      class="list-item"
      is="grocery-item"
      v-for="grocery in groceries"
      :key="grocery.id"
      :grocery="grocery"
      @save="save"
      @remove="remove"
      @check="check">
    </li>
  </transition-group>
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
      this.$emit('check', item)
    }
  }
}
</script>

<style scoped>
.list-item {
  transition: 0.4s;
}
.list-enter {
  opacity: 0;
  transform: translateX(30px);
}

.list-enter-to {
  //transform: translateX(30px);
}

.list-enter-active {
  //transition: all 0.1s;
  //transform: translateY(-15px);
}

.list-leave-to {
  transition: all 0.35s;
  opacity: 0;
}
.list-leave-active {
  //transform: translateX(30px);

}
</style>
