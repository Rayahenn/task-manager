<template>
  <div id="app">
    <div class="wrapper">
      <div class="taskList" v-for="board in boards" :key="board.id">
        <h1>{{ board.name }}</h1>
        <div class="taskItem" v-for="task in taskList" :key="task.id" :board="task.board_id" v-if="task.board_id === board.id">
          <h1>{{ task.name }}</h1>
        </div>
      </div>
      



    </div>
  </div>
</template>

<script>
//import TaskItem from '@/components/TaskItem';

export default {
  name: 'App',
  //components: { TaskItem }
  data() {
    return {
       taskList: [
                {
                    id: 1,
                    board_id: 1,
                    name: "Testowy0"
                },
                {
                    id: 2,
                    board_id: 1,
                    name: "Testowy1"
                },
                {
                    id: 3,
                    board_id: 2,
                    name: "Testowy2"
                },
                {
                    id: 4,
                    board_id: 3,
                    name: "Testowy3"
                }
            ],
        boards: [
          {
            id: 1,
            name: "Realizowane"
          },
           {
            id: 2,
            name: "Wstrzymane"
          },
           {
            id: 3,
            name: "Do realizacji"
          },
           {
            id: 4,
            name: "Rozwiązane"
          },
           {
            id: 5,
            name: "Zakończone"
          }
        ]
  }
  }
}
</script>

<style>
  * {
    box-sizing: border-box;
  }

  body {
    font-family: Arial;
    margin: 0;
    padding: 0;
  }

  .wrapper { 
    display: flex;
    position: relative;
   justify-content: space-between;
    height: 100vh;
    width: 100%;
    background-color: rgb(47, 47, 197);
    
    color: white;
    margin: 0;
  }

  .taskList {
    height: auto;
    position: relative;
    display: inline-block;
    width: 17%;
    background-color: red;
    padding: 0 15px;
    margin: 0 0 auto;
    min-height: 200px;
    
  }
  .taskItem {
        position: relative;
        display: flex;
        
        justify-content: center;
        width: 100%;
        border: 2px solid black;
        height: 100px;
        margin: 10px 0;
        font-size: 13px
  }
</style>
