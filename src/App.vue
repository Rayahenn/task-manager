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
      //  taskList: [
      //           {
      //               id: 1,
      //               board_id: 1,
      //               name: "Testowy0"
      //           },
      //           {
      //               id: 2,
      //               board_id: 1,
      //               name: "Testowy1"
      //           },
      //           {
      //               id: 3,
      //               board_id: 2,
      //               name: "Testowy2"
      //           },
      //           {
      //               id: 4,
      //               board_id: 3,
      //               name: "Testowy3"
      //           }
      //       ],
        // boards: [
        //   {
        //     id: 1,
        //     name: "Realizowane"
        //   },
        //    {
        //     id: 2,
        //     name: "Wstrzymane"
        //   },
        //    {
        //     id: 3,
        //     name: "Do realizacji"
        //   },
        //    {
        //     id: 4,
        //     name: "Rozwiązane"
        //   },
        //    {
        //     id: 5,
        //     name: "Zakończone"
        //   }
        // ]
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
    background-color: rgb(47, 47, 197);
    
    color: white;
    margin: 0;
  }

</style>
