<template lang="pug">
  .card
    div(v-if="!edited")  
      .card-title {{ todo.title }}
      .card-article {{ todo.content  }}
      .card-date {{ todo.date }}
      .card-action
        button.btn(@click.prevent="editTodo") Edit
        button.btn(@click.prevent="removeTodos(todo.key)") Revome
    div(v-else)
      input(v-model="title").sidebar-form_title
      textarea(v-model="content").sidebar-form_content
      .card-date {{ todo.date }}
      .card-action
        button.btn(@click.prevent="updateTodo(todo.key)") Update
</template>

<script>
  // import eventBus from '../main';

  export default {
    name: 'Card',
    props: ['todo'],
    data() {
      return {
        edited: false,
        title: '',
        content: '',
      };
    },
    methods: {
      editTodo() {
        this.edited = !this.edited;
        this.title = this.todo.title;
        this.content = this.todo.content;
      },
      updateTodo(key) {
        const data = {
          keys: key,
          title: this.title,
          content: this.content,
        };
        this.$emit('updatetodo', data);
        this.edited = !this.edited;
      },
      removeTodos(key) {
        this.$emit('removetodos', key);
      },
    },
  };
</script>

<style lang="sass" scoped>
  @import "./../base.sass"

  .sidebar-form_title ,.sidebar-form_content
    width: 100%
    font-size: 1.2rem
    margin-bottom: 5px
    color: $color-secondary
  .sidebar-form_content
    min-height: 300px

  
  .card
    display: flex
    flex-direction: column
    background-color: $color-card
    width: calc(1000px / 3.1)
    min-height: 200px
    padding: 20px 10px 10px 10px
    margin-bottom: 10px
    border-top: 5px solid $color-secondary
    .card-title
      font-size: 1.5rem
      text-transform: uppercase
      color: $color-header
      font-weight: bold
      // text-align: center
      &::after
        content: ''
        display: block
        border: 5px solid $color-secondary
        width: 50px
        margin-top: 5px
    .card-article,.card-user,.card-action,.card-date
      // border: 1px solid #333
      margin-top: 10px
    .card-article
      flex: 1
    .card-date
      text-align: right
    .btn
      color: $color-header
      padding: 5px 10px
      border: 1px solid $color-secondary
      transition: all 0.5s
      margin-right: 5px
      &:hover
        border: 1px solid rgba($color-secondary , 0)
        background-color: $color-secondary
        color: $color-card
</style>