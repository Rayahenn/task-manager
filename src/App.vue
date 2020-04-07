<template>
  <div id="app">
    <div class="wrapper">
      <TaskList />
    </div>
  </div>
</template>

<script>

import TaskList from '@/components/TaskList';

export default {
  name: 'App',
  components: { TaskList },
  data() {
    return {
  
  }
  }
}
</script>

<style lang="scss">
  * {
    box-sizing: border-box;
  }

  body {
    font-family: Arial;
    margin: 0;
    padding: 0;
  }

  .wrapper { 

    position: relative;

    height: 100vh;
    width: 100%;
    background-color: rgb(40, 40, 66);
    
    color: white;
    margin: 0;
  }

</style>
