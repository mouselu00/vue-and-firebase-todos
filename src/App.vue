<template>
  <div id="app">
    <!-- <hello></hello> -->
    <Navs></Navs>
    <div class="container">
      <div class="cards">
        <Card 
          v-for="todo in todos" 
          :key="todo"
          ></Card>
      </div>
    </div>
    <Sidebars></Sidebars>
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
      todos: [1, 2, 3, 4, 5],
    };
  },
  components: {
    // Hello,
    Navs,
    Card,
    Sidebars,
    Dialogs,
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
