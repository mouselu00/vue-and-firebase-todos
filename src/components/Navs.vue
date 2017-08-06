<template lang="pug">
  header
    .header
      .header-brand
        p LoGo
      nav.header-nav
        div(v-if="logstate")
          a(href='#' @click.prevent="toggleDialog('signup')").header-nav_link SIGN UP
          a(href='#' @click.prevent="toggleDialog('signin')").header-nav_link SIGN IN
        div(v-else)
          a(href='#' @click.prevent="toggleSidebar").header-nav_link NEW TASK
          a(href='#' @click.prevent="logoutHandle").header-nav_link LOGOUT
</template>
<script>
import eventBus from '../main';

export default {
  name: 'Navs',
  props: ['logstate'],
  methods: {
    // emit Dialog component to toggle dialog
    toggleDialog(type) {
      // in Dialog.vue
      eventBus.$emit('toggleDialog', type);
    },
    // emit Sidebar component to toggle sidebar
    toggleSidebar() {
      // in Sidebars.vue
      eventBus.$emit('toggleSidebar');
    },
    // emit parent methods
    logoutHandle() {
      this.$emit('logouthandle');
    },
  },
};
</script>
<style lang="sass" scope>
  @import "./../base.sass"

  header
    width: 100%
    min-height: 200px
    background-color: $color-header
    .header
      margin: 0px auto
      max-width: 1000px
      background-color: $color-header
      display: flex
      justify-content: space-between
      align-items: flex-end
      position: relative
      top: 100px
      .header-brand
        background-color: #fff
        display: inline-block
        font-size: 3rem
      .header-nav
        margin: 0px
        padding: 0px
        .header-nav_link
          margin-left: 5px
          border-bottom: 1px solid $color-link
          margin: 0px 5px
          transition: all 0.5s
          &:hover
            border-bottom: 20px solid $color-link
   
</style>


  