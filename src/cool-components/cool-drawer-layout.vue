<style lang="stylus" scoped>

  .cool-drawer-layout
    position: absolute;
    width: 100vw;
    height: 100vh;

  .main-content-container 
    position: absolute;
    top: 0
    right: 0
    bottom: 0
    left: 0
    transition: all .4s ease-in-out;
  
  .cool-drawer-layout:not([narrow]) 
    background-color: blue;

    & .main-content-container {
      margin-left: 240px;
    }


  .cool-drawer-layout[narrow] #drawer {
    position: fixed;
    background-color: grey;
  }

  // .drawer-container {
  //   height: 100%;
  //   width: 240px;
  //   background: #212121;
  //   color: #ddd;
  // }
</style>

<template id="coolDrawerLayout">

<div class="cool-drawer-layout">

  <slot id="drawer" name="drawer"></slot>

  <div class="main-content-container">
    <slot></slot>
  </div>
</div>


</template>

<script>
// Load the core build.
import _ from 'lodash'

export default {
  name: 'coolDrawerLayout',
  props: {
    narrow: Boolean,
    windowWidth: Number,
    responsiveWidth: {
      type: Number,
      default: 640,
      validator: function (value) {
        return value > 350
      }
    }
  },
  data: function () {
    return {
      drawerWidth: String
    }
  },

  created () {
    console.log('cool-drawer-layout creation started...')

    // HERE WE OBSERVE THE DATA AND INIT THE EVENTS
    this._setNarrowAttr = this._setNarrowAttr.bind(this)

    this._addEventListeners()
    console.log('cool-drawer-layout creation fineshed...')
  },

  mounted () {
    this.drawerWidth = this.$parent.$refs.drawer.width
    this._setPageMargin()
    this._setNarrowAttr()
    this._setDrawerPersistanse()
  },

  methods: {
    isNarrow: function () {
      return window.innerWidth <= this.responsiveWidth
    },

    _setPageMargin: function () {
      if (!this.isNarrow()) {
        this.$el.querySelector('.main-content-container').style.marginLeft = this.drawerWidth
      } else {
        this.$el.querySelector('.main-content-container').style.marginLeft = 0
      }
    },

    _setNarrowAttr: function () {
      return this.isNarrow()
        ? this.$el.setAttribute('narrow', '')
        : this.$el.removeAttribute('narrow')
    },

    _setDrawerPersistanse () {
      return this.isNarrow()
        ? this.$parent.$refs.drawer._unsetSelfPersistant()
        : this.$parent.$refs.drawer._setSelfPersistant()
    },

    _addEventListeners: function () {
      console.log('Adding Event Listeners')
      window.addEventListener('resize', _.debounce(function () {
        this._setPageMargin()
        this._setNarrowAttr()
        this._setDrawerPersistanse()
      }.bind(this), 180))
    }
  }
}
</script>
