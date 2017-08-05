<template>
  <div id="app">
    <Navs @logouthandle="logoutHandle" :logstate="logout"></Navs>
    <div class="container">
      <div class="cards">
        <h2 v-show="todos.length <= 0">Create Todo</h2>
        <h2 v-show="!logout <= 0">Sign up</h2>
        <Card v-for="todo in todos" :key="todo.key  " :todo="todo" @removetodos="removeTodos" @updatetodo="updateTodo"></Card>
      </div>
    </div>
    <Sidebars @addtodo="addTodo"></Sidebars>
    <Dialogs @signuphandle="signupHandle" @signinhandle="signinHandle"></Dialogs>
  </div>
</template>

<script>
/* eslint-disable */

import firebase from 'firebase';

import Navs from './components/Navs';
import Card from './components/Card';
import Sidebars from './components/Sidebars';
import Dialogs from './components/Dialogs';

import eventBus from './main';

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
      logout: true,
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
    // create new todo to firebase
    addTodo(data = null) {
      const userID = firebase.auth().currentUser.uid;
      const dbRef = firebase.database().ref(`users/${userID}/todos`);
      dbRef.push(data);
    },
    // remove todo from firebase
    removeTodos(k) {
      const userID = firebase.auth().currentUser.uid;
      firebase.database().ref(`users/${userID}/todos/${k}`).remove();
    },
    // update todo to firebase
    updateTodo(data) {
      const userID = firebase.auth().currentUser.uid;
      firebase.database().ref(`users/${userID}/todos/${data.keys}`).update({ title: data.title, content: data.content });
    },
    // create new user
    signupHandle(signUpData) {
      if (signUpData.password == signUpData.passwordComfirm) {
        firebase.auth().createUserWithEmailAndPassword(signUpData.email, signUpData.password)
          .then((res) => {
            eventBus.$emit('toggleDialog');
          })
          .catch((err) => {
            console.log(err);
          })
      } else {
        alert('password not some!');
      }
    },
    // sign in
    signinHandle(signinData) {
      firebase.auth().signInWithEmailAndPassword(signinData.email, signinData.password)
        .then((res) => {
          eventBus.$emit('toggleDialog');
        })
        .catch((err) => {
          alert(err);
        });
    },
    // logout user
    logoutHandle() {
      firebase.auth().signOut();
    },
  },
  created() {
    firebase.auth().onAuthStateChanged((user) => {
      if (user) {
        const userID = firebase.auth().currentUser.uid;
        firebase.database().ref(`users/${userID}/todos`).on('value', (res) => {
          const userData = res.val();
          const dataArray = [];
          for (var key in userData) {
            userData[key].key = key;
            dataArray.push(userData[key]);
          }
          this.todos = dataArray;
          this.logout = false;
        });
      } else {
        this.logout = true;
        this.todos = [];
      }
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
