<template>
  <div>{{ resourceName }} : <button v-on:click="decrement()">-</button> {{ count }} <button v-on:click="increment()">+</button></div>
</template>

<script>
export default {
  name: 'Resource',
  props: {
    resourceName: String
  },
  data() {
    return {
      count: 0
    }
  },
  methods: {
    increment() {
      this.count += 1
    },
    decrement() {
      if (this.count > 0) {
        this.count -= 1
      }
    }
  }
}
</script>