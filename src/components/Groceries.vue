<template>
  <div>
    <grocery-list-header></grocery-list-header>
    <section class="section">
      <grocery-form @submit="add"></grocery-form>
      <grocery-list
        @update="update"
        @remove="remove"
        @check="check"
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
          unit: 'None',
          done: false
        },
        {
          id: 2,
          name: 'Cherries',
          quantity: 0,
          unit: 'None',
          done: false
        },
        {
          id: 3,
          name: 'Oranges',
          quantity: 0,
          unit: 'None',
          done: false
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
      this.groceries = [elem].concat(this.groceries)
    },
    nextId () {
      this.lastId += 1
      return this.lastId
    },
    update (item) {
      this.groceries = this.groceries.map(i => {
        if (i.id === item.id) {
          return Object.assign(i, item)
        } else {
          return i
        }
      })
    },
    remove (item) {
      this.groceries = this.groceries.filter(i => i.id !== item.id)
    },
    check (item) {
      this.groceries = this.groceries.map(i => {
        if (i.id === item.id) {
          item = Object.assign(item, {done: !item.done})
          return item
        }
        return i
      }).sort((a, b) => {
        if (a.done && !b.done) {
          return 1
        }

        if (!a.done && b.done) {
          return -1
        }
        return 0
      })
    }
  }

}
</script>

<style scoped>

</style>
