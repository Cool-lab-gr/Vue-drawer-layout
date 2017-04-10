<style lang="stylus" scoped>
  .cool-header {
    display: block;
    min-height: 56px;
  }
</style>

<template>
  <div class="cool-header">
    <slot></slot>
  </div>
</template>

<script>
  export default {
    name: 'coolHeader'
  }
</script>
