<style lang="styl" scoped>
  /* .icon-button[hidden] {
  //   display: none !important;
  // } */
  .icon-button {
    display: inline-flex;
    width: 40px;
    height: 40px;
    align-items: center;
    justify-content: center;
    border-radius: 50%;
    cursor: pointer;
    margin-right: 8px;
  }
  .icon-button:focus,
  .icon-button:hover{
    background-color: rgba(0,0,0,0.4);
  }
</style>
<template>
  <div class="icon-button">
    <span class="material-icons">{{icon}}</span>
  </div>
</template>

<script>
  export default {
    name: 'iconButton',

    props: {
      icon: {
        type: String,
        required: true
      }
    },

    mounted () {
      this.$el.setAttribute('tabindex', 0)
    }
  }
</script>
