<template>
    <div class="tasks">
        <div class="taskItem" 
        v-for="task in taskList" 
        :key="task.id" 
        :board_id="task.board_id"
        :class="{ isFavourite: favourite}"
        v-if="task.board_id == board_id"
        >
          <h1>{{ task.name }}</h1>
          <i class="fa fa-star-o" aria-hidden="true" 
          @click="toggleFavourite"
          ></i>
        </div>
    </div>
</template>

<script>

export default {
    
    props: {
        board_id: Number,
    },
    data() {
        return{
            favourite: false,
            taskList: [
                {
                    id: 1,
                    board_id: 0,
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
                },
                {
                    id: 4,
                    board_id: 4,
                    name: "Testowy4"
                }
            ],
        }
    },
    methods: {
        toggleFavourite() {
                this.favourite = !this.favourite
        }
    },
}
</script>

<style lang="scss">


  .taskItem {
        position: relative;
        display: flex;
        justify-content: center;
        width: 100%;
        border: 2px solid black;
        height: 100px;
        margin: 10px 0;
        font-size: 13px;
        i {
            position: absolute;
            top: 60%;
            right: 20px;
            font-size: 20px;
            height: 20px;
            cursor: pointer;

        }
  }
  .isFavourite {
            border-left: 5px solid blue;
        }
</style>