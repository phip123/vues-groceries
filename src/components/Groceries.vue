<template>
  <div>
    <grocery-list-header></grocery-list-header>
    <section class="section">
      <grocery-form @submit="add"></grocery-form>
      <grocery-list
        @update="update"
        :groceries="groceries"
      ></grocery-list>
    </section>
  </div>

</template>

<script>
import GroceryList from './GroceryList'
import GroceryForm from './GroceryForm'
import GroceryListHeader from './GroceryListHeader'

export default {
  components: {
    GroceryListHeader,
    GroceryForm,
    GroceryList
  },
  name: 'groceries',
  data () {
    return {
      lastId: 3,
      groceries: [
        {
          id: 1,
          name: 'Apple',
          quantity: 0,
          unit: 'None'
        },
        {
          id: 2,
          name: 'Cherries',
          quantity: 0,
          unit: 'None'
        },
        {
          id: 3,
          name: 'Oranges',
          quantity: 0,
          unit: 'None'
        }
      ]
    }
  },
  methods: {
    add (element) {
      const elem = {
        id: this.nextId(),
        ...element
      }
      console.log(elem)
      console.log(this.groceries)
      this.groceries.push(elem)
    },
    nextId () {
      this.lastId += 1
      return this.lastId
    },
    update (item) {
      this.groceries = this.groceries.map(i => {
        if (i.id === item.id) {
          return item
        } else {
          return i
        }
      })
    }
  }

}
</script>

<style scoped>

</style>
