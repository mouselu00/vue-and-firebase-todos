<template>
  <div id="app">
    <!-- <hello></hello> -->
    <Navs></Navs>
    <div class="container">
      <Cards></Cards>
    </div>
    <Sidebars></Sidebars>
    <Dialogs></Dialogs>
  </div>
</template>

<script>
// import Hello from './components/Hello';
import Navs from './components/Navs';
import Cards from './components/Cards';
import Sidebars from './components/Sidebars';
import Dialogs from './components/Dialogs';


export default {
  name: 'app',
  components: {
    // Hello,
    Navs,
    Cards,
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
    
</style>
