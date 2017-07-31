<template lang="pug">
  .dialog(:class="{'close-dialog': closeDialog}")
    .dialog-title
      p {{ title }}
    .dialog-form
      input(type="email" placeholder="@mail.com")
      input(type="password" placeholder="Password")
      input(type="password" placeholder="Password Comfirm")
    .dialog-action
      button.btn SIGN    
      button.btn.dialog-btn_close(@click.prevent="closeDialog =!closeDialog") CLOSE
</template>

<script>
export default {
  name: 'Dialog',
  data() {
    return {
      title: 'SIGN UP',
      closeDialog: false,
    };
  },
  methods: {
  },
};
</script>


<style lang="sass" scoped>
  @import ".././base.sass"

  .dialog
    position: absolute
    top: 50%
    left: 50%
    transform: translate(-50% , -50%)
    background-color: $color-secondary
    width: 500px
    height: 400px
    padding: 20px
    transition: all 0.5s
    &.close-dialog
      display: none
    .dialog-title
      display: block
      color: $color-link
      font-size: 2rem
      margin: 20px 0px
      &::after
        content: ''
        display: block
        border: 5px solid $color-link
        width: 50px
        margin-top: 5px
    .dialog-form
      width: 100%
      height: 60%
      // border: 1px solid #333
      input
        display: block
        width: 100%
        height: 20%
        font-size: 1.4rem
        border: none
        margin-top: 10px
        background-color: $color-link
        color: $color-secondary
        outline: none
        border-bottom: 3px solid $color-header
        text-align: center
    .dialog-action
      text-align: right
      button
        border: 1px solid $color-link
        color: $color-link
        &:hover
          border: 1px solid $color-secondary
          color: $color-secondary
          background-color: $color-link
</style>
