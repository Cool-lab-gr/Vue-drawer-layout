<style lang="styl" scoped>
  .cool-toolbar {
    display: flex;
    height: 64px;
    align-items: center;
    margin: 0 16px;
  }
  .title {
    font-size: 20px;
  }
  .spacer {
    flex: 1;
  }
</style>

<template>
  <div class="cool-toolbar">
    <slot></slot>
  </div>
</template>

<script>
  export default {
    name: 'coolToolbar'
  }
</script>
