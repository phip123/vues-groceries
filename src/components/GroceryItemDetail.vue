<template>
  <div class="card">
    <div class="card-content">
      <div class="content is-medium">
        <p>{{grocery.name}}</p>
      </div>
    </div>
    <footer class="card-footer">
      <a
        @click.prevent="check"
        class="card-footer-item">Got it!</a>
      <a
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
    props: ['grocery'],
    name: 'grocery-item-detail',
    methods: {
      check() {
        this.$emit('check')
      },
      edit() {
        this.$emit('edit')
      },
      remove() {
        this.$emit('remove')
      }
    }
  }
</script>

<style scoped>

</style>
