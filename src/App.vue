<template>
  <div id="app">
    <!-- <hello></hello> -->
    <Navs></Navs>
    <div class="container">
      <Cards></Cards>
    </div>
    <Sidebars></Sidebars>
    <Dialog></Dialog>
  </div>
</template>

<script>
// import Hello from './components/Hello';
import Navs from './components/Navs';
import Cards from './components/Cards';
import Sidebars from './components/Sidebars';
import Dialog from './components/Dialog';

export default {
  name: 'app',
  components: {
    // Hello,
    Navs,
    Cards,
    Sidebars,
    Dialog,
  },
};
</script>

<style lang="sass">
  #app 
    width: 100%
    min-height: 500px
    background: #ccc            
    
</style>
