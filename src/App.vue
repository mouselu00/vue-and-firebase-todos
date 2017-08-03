<template>
  <div id="app">
    <!-- <hello></hello> -->
    <Navs></Navs>
    <div class="container">
      <div class="cards">
        <h2 v-show="todos.length <= 0">Create Todo</h2>
        <Card 
          v-for="todo in todos" 
          :key="todo.title"
          :todo="todo"
          ></Card>
      </div>
    </div>
    <Sidebars @addtodo="addTodo"></Sidebars>
    <Dialogs></Dialogs>
  </div>
</template>

<script>
// import Hello from './components/Hello';
import Navs from './components/Navs';
import Card from './components/Card';
import Sidebars from './components/Sidebars';
import Dialogs from './components/Dialogs';


export default {
  name: 'app',
  data() {
    return {
      todos: [],
    };
  },
  components: {
    // Hello,
    Navs,
    Card,
    Sidebars,
    Dialogs,
  },
  methods: {
    // method from addtodo by Sidebars.vue
    addTodo(data = null) {
      this.todos.push(data);
    },
  },
};
</script>

<style lang="sass">
  #app 
    width: 100%
    min-height: 500px
    background: #ccc            
    .cards
      width: 100%
      height: auto
      padding: 0px
      margin: 0px
      display: flex
      justify-content: space-around
      flex-wrap: wrap
      align-items: flex-start
      margin-top: 50px    
</style>
