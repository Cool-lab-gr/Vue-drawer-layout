<style lang="stylus" scoped>

  .cool-drawer-container 
    position: fixed;
    background: #212121;
    color: #ddd;
    height: 100%;
    max-width: 90%;
    transition: transform .4s ease-in-out;
    transform: translateX(-100%)

  .cool-drawer-container[persistant]
    position: absolute
    transform: translateX(0)

  .cool-drawer-container[opened]
    transform: translateX(0)

</style>

<template id="coolDrawer">

<div class="cool-drawer-container">
  <slot></slot>
</div>


</template>

<script>
export default {
  name: 'coolDrawer',
  props: {
    width: {
      type: String,
      default: '240px'
    },
    screenSide: {
      type: String,
      value: 'left'
    }
  },

  mounted () {
    this.$el.style.width = this.width
  },

  methods: {
    open () {
      this.$el.setAttribute('opened', '')
    },
    _setSelfPersistant () {
      this.$el.setAttribute('persistant', '')
    },
    _unsetSelfPersistant () {
      this.$el.removeAttribute('persistant')
    }
  }
}
</script>
