<template>

    <cool-drawer-layout ref="drawerLayout" id="app" :responsive-width="responsiveWidth">
    
      <cool-drawer ref="drawer" id="drawer" slot="drawer" screen-side="right" width="440px">
        Drawer Content
      </cool-drawer>
    
      <cool-header>
        <cool-toolbar>
          <icon-button ref="drawerToggler" icon="menu"></icon-button>
          
          <span class="title">coolLab</span>
        </cool-toolbar>
      </cool-header>
    
      <router-view></router-view>
    </cool-drawer-layout>




</template>

<script>
import coolDrawerLayout from './cool-components/cool-drawer-layout'
import coolDrawer from './cool-components/cool-drawer'
import coolHeader from './cool-components/cool-header'
import coolToolbar from './cool-components/cool-toolbar'

import iconButton from './cool-components/icon-button'

export default {
  name: 'app',
  components: {
    coolDrawerLayout, coolDrawer, coolHeader, coolToolbar, iconButton
  },
  data: function () {
    return {
      responsiveWidth: 1140,
      _isNarrow: Boolean
    }
  },
  watch: {
    _isNarrow: function (newValue, oldValue) {
      console.log(newValue)
      console.log(oldValue)
    }
  },
  mounted () {
    console.log(this.$refs.drawer)
    this.isNarrow()
  },
  methods: {
    isNarrow () {
      this._isNarrow = window.innerWidth <= this.responsiveWidth
      console.log(this._isNarrow)
      return this._isNarrow
    }
  }
}
</script>

<style lang="stylus">
  #app
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;

  [hidden]
    display: none !important;

</style>
