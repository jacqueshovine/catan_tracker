<template>
  <div>{{ name }}</div>
</template>

<script>
export default {
  name: 'Resource', // Component name
  props: {
    name: String, // Resource name
  }
}
</script>