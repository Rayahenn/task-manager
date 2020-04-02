<template>
    <div class="tasks">
        <div class="taskItem" 
        v-for="task in taskList" 
        :key="task.id" 
        :board_id="task.board_id"
        :class="{ isFavourite: favourite}"
        v-if="task.board_id == board_id"
        >
          <h1 v-if="!isEditing" class="taskTitle">{{ task.name }}</h1>

          <input type="text" 
          class="editTask"
          v-model="task.name" 
          v-if="isEditing"
          >
        
            <div class="date">
                {{ time }}
            </div>
          <i class="fa fa-pencil-square-o edit" 
          aria-hidden="true" 
          @click="handleEdit"
          />

          <i class="fa fa-star-o favourite" 
          aria-hidden="true" 
          @click="toggleFavourite"
          />

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
            isEditing: false,
            time: null,  
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
        },
        handleEdit() {
            this.isEditing = !this.isEditing;
        },
        getDate() {
            var currentTime = new Date().toLocaleString();
            this.time = currentTime
        }
    },
    mounted() {
        this.getDate()
    },
}
</script>

<style lang="scss">
    .taskTitle {
        height: 40px;
        margin: 10px;
    }

    .date {
        height: auto;
        width: auto;
        font-size: 12px;
        position: absolute;
        top: 70%;
        left: 5%;
    }
    .editTask {
        position: absolute;
        height: 40px;
        width: 80%;
        margin: 10px auto;
        line-height: 100%;
        background-color: transparent;
        border: none;
        color: white;
        font-size: 20px;
        border: 2px solid gray;
        text-align: center;
        &:focus {
            border: 2px solid blue;
        }
    }

  .taskItem {
        position: relative;
        display: flex;
        justify-content: center;
        width: 100%;
        border: 2px solid black;
        height: 100px;
        margin: 10px 0;
        font-size: 13px;
        i.favourite {
            position: absolute;
            top: 60%;
            right: 20px;
            font-size: 20px;
            height: 20px;
            cursor: pointer;
        }
        i.edit {
            position: absolute;
            top: 60%;
            right: 50px;
            font-size: 20px;
            height: 20px;
            cursor: pointer;
        }
  }
  .isFavourite {
            border-left: 5px solid blue;
        }
</style>