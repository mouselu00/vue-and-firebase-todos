<template>
  <div id="app">
    <!-- <hello></hello> -->
    <Navs></Navs>
    <div class="container">
      <div class="cards">
        <h2 v-show="todos.length <= 0">Create Todo</h2>
        <Card 
          v-for="todo in todos" 
          :key="todo.key  "
          :todo="todo"
          @removetodos="removeTodos"
          @updatetodo="updateTodo"
          ></Card>
      </div>
    </div>
    <Sidebars @addtodo="addTodo"></Sidebars>
    <Dialogs></Dialogs>
  </div>
</template>

<script>
/* eslint-disable */
// import Hello from './components/Hello';

import firebase from 'firebase';

import Navs from './components/Navs';
import Card from './components/Card';
import Sidebars from './components/Sidebars';
import Dialogs from './components/Dialogs';

// firebase config
const config = {
  apiKey: 'AIzaSyCPa1K505ZFulvXbSJbYaSVEq0taCSo6AM',
  authDomain: 'todos-a07d6.firebaseapp.com',
  databaseURL: 'https://todos-a07d6.firebaseio.com',
  projectId: 'todos-a07d6',
  storageBucket: 'todos-a07d6.appspot.com',
  messagingSenderId: '1088273962315',
};
firebase.initializeApp(config);

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
      const dbRef = firebase.database().ref();
      dbRef.push(data);
    },
    removeTodos(k) {
      firebase.database().ref(k).remove();
    },
    updateTodo(data) {
      firebase.database().ref(data.keys).update({title: data.title, content: data.content});
    },
  },
  created() {
    firebase.database().ref().on('value', (res) => {
      const userData = res.val();
      const dataArray = [];
      for (var key in userData) {
        userData[key].key = key;
        dataArray.push(userData[key]);  
      }
      this.todos = dataArray;
    });
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
