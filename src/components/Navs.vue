<template lang="pug">
  header
    .header
      .header-brand
        p LoGo
      nav.header-nav
        a(href='#').header-nav_link NEW TASK
        a(href='#').header-nav_link SIGN UP
        a(href='#').header-nav_link SIGN IN
        a(href='#').header-nav_link LOGOUT
</template>
<script>
export default {
  name: 'Navs',
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


  