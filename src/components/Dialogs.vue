<template lang="pug">
  div(v-if="types == 'signup'")
    .dialog(:class="{'close-dialog': closeDialog}")
      .dialog-title
        p Sign Up
      .dialog-form
        input(
          type="email" 
          placeholder="@mail.com" 
          v-model="email")
        input(
          type="password" 
          placeholder="Password" 
          v-model="password")
        input(
          type="password" 
          placeholder="Password Comfirm"
          v-model="passwordComfirm")
      .dialog-action
        button.btn(@click.prevent="signupHandle") SIGN UP
        button.btn.dialog-btn_close(@click.prevent="closeDialog =!closeDialog") CLOSE
  div(v-else)
    .dialog(:class="{'close-dialog': closeDialog}")
      .dialog-title
        p Sign In
      .dialog-form
        input(
          type="email" 
          placeholder="@mail.com"
          v-model="email")
        input(
          type="password" 
          placeholder="Password"
          v-model="password")
      .dialog-action
        button.btn(@click.prevent="signinHandle") SIGN IN
        button.btn.dialog-btn_close(@click.prevent="closeDialog =!closeDialog") CLOSE
</template>

<script>
import eventBus from '../main';

export default {
  name: 'Dialogs',
  data() {
    return {
      closeDialog: true,        // state to toggle dialog
      types: null,              // state to togle signup or signin dialog template
      password: null,           // signup or sign in password state
      passwordComfirm: null,    // signup password comfirm state
      email: null,              // signup or signin email state
    };
  },
  methods: {
    // to toggle dialog and recognize types of template to show
    toggleDialog(type) {
      this.closeDialog = !this.closeDialog;
      this.types = type;
    },
    // emit parent method - signup
    signupHandle() {
      const sinUpData = {
        password: this.password,
        passwordComfirm: this.passwordComfirm,
        email: this.email,
      };
      this.$emit('signuphandle', sinUpData);
      this.password = null;
      this.passwordComfirm = null;
      this.email = null;
    },
    // emit parent methods - signin
    signinHandle() {
      const signInData = {
        password: this.password,
        email: this.email,
      };
      this.$emit('signinhandle', signInData);
      this.password = null;
      this.email = null;
    },
  },
  // hook
  created() {
    eventBus.$on('toggleDialog', this.toggleDialog);    // listen bro component to toggle Dialog
  },
  beforeDestroy() {
    eventBus.$off('toggleDialog');
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
