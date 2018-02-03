<template>
  <div class="card" v-bind:class="doned">
    <div class="card-content">
      <div class="content is-medium">
        <p>{{quantity}} {{grocery.name}}</p>
      </div>
    </div>
    <footer class="card-footer">
      <a
        @click.prevent="check"
        class="card-footer-item">{{checkText}}</a>
      <a
        v-show="!grocery.done"
        @click.prevent="edit"
        class="card-footer-item">Edit</a>
      <a
        @click.prevent="remove"
        class="card-footer-item">Delete</a>
    </footer>
  </div>
</template>

<script>
export default {
  props: {
    grocery: {
      type: Object,
      default: function () {
        return {
          id: -1,
          name: '',
          quantity: -1,
          unit: 'None',
          done: false
        }
      }
    }
  },
  name: 'grocery-item-detail',
  methods: {
    check () {
      this.$emit('check')
    },
    edit () {
      this.$emit('edit')
    },
    remove () {
      this.$emit('remove')
    }
  },
  computed: {
    quantity: function () {
      let s = ''
      if (this.grocery.quantity && this.grocery.quantity !== 0) {
        s += this.grocery.quantity + ' '
      }

      if (this.grocery.unit && this.grocery.unit !== 'None') {
        s += this.grocery.unit + ' of '
      }

      return s
    },
    doned: function () {
      return {done: this.grocery.done}
    },
    checkText: function () {
      if (this.grocery.done) {
        return "Didn't get it..."
      } else {
        return 'Got it!'
      }
    }
  }
}
</script>

<style scoped>
.done {
  opacity: 0.5;
}

</style>
