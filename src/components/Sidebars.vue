<template lang="pug">
  .sidebar(:class="{'show-sidebar': showSidebar}")
    .sidebar-title
      p Create Task
      button(@click="showSidebar = !showSidebar") X
    .sidebar-form
      input.sidebar-form_title(v-model="todo.title" type="text" placeholder="Title...")
      input.sidebar-form_date(v-model="todo.date" type="date" placeholder="Date...")
      textarea.sidebar-form_content(v-model="todo.content" placeholder="Contents...")
      button.btn(@click.prevent="add_todos") Submit
      p.warning(v-show="error") All Field Is Required!!
</template>

<script>
import eventBus from '../main';

export default {
  name: 'Sidebars',
  data() {
    return {
      showSidebar: false, // toggle to show sidebar state
      error: false,       // show error msg toggle state
      todo: {
        title: null,      // new todo title state
        date: null,       // new todo date state
        content: null,    // new todo content state
      },
    };
  },
  methods: {
    // toggle sidebar state
    toggleSidebar() {
      this.showSidebar = !this.showSidebar;
    },
    // emit to parent method - add new todo
    add_todos() {
      if (this.todo.title && this.todo.date && this.todo.content) {
        this.error = false;
        const trimTodo = {
          title: this.todo.title.trim(),
          date: this.todo.date.trim(),
          content: this.todo.content.trim(),
        };
        this.$emit('addtodo', trimTodo);
        this.todo.title = null;
        this.todo.date = null;
        this.todo.content = null;
        this.toggleSidebar();
      } else {
        this.error = true;
      }
    },
  },
  // hook
  created() {
    eventBus.$on('toggleSidebar', this.toggleSidebar);    // listen bro component to toggle sidebar
  },
  beforeDestroy() {
    eventBus.$off('toggleSidebar');
  },

};
</script>

<style lang="sass" scoped>
  
  @import ".././base.sass"

  .sidebar
    display: inline-block
    width: 300px
    min-height: 100%
    background-color: #fff
    position: absolute
    top: 0px
    padding: 10px
    box-shadow: 10px 0px 10px 0px rgba(#000 , 0.3)
    transition: transform 0.5s
    transform: translateX(-105%)
    &.show-sidebar
      transform: translateX(0%)
    .sidebar-title
      width: 100%
      color: $color-secondary
      &::after
        content: ''
        display: block
        border: 5px solid $color-secondary
        width: 50px
        margin-top: 5px
      p
        display: inline-block
        width: 80%
        font-size: 2rem
      button
        border: 1px solid $color-secondary
        font-size: 2rem
        width: 50px
        height: 100%
        color: $color-secondary
        transition: all 0.3s
        &:hover
          background-color: $color-secondary
          color: #fff
    .sidebar-form
      margin-top: 30px
      .sidebar-form_title , .sidebar-form_date , .sidebar-form_content
        width: 100%
        font-size: 1.2rem
        margin-bottom: 5px
        color: $color-secondary
      .sidebar-form_content
        min-height: 300px
      .warning
        color: red
        font-weight: bold
</style>

