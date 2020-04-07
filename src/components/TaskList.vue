<template>
    <div class="board">
        <draggable v-model="boards" class="dragList" >
            <div class="taskList" v-for="(board, index) in boards" :key="board.id" >
                <h1>{{ board.name }}</h1>
                    <TaskItem :board_id="board.id" :newTask="newTask" />
                <div class="addItem">
                    <div class="add" @click="openNewItem(index)" :class="{ active: board.active}" v-if="!board.addingItem">+</div>
                    <div class="newItem" v-else>
                        <input type="text" 
                        class="itemName" 
                        placeholder="Wpisz nazwe zadania..." 
                        v-model="newTaskName">
                        <div class="apply" @click="addNewTask(index)" >Zatwierdź</div>
                        <div class="cancel" @click="closeNewItem(board.id)">Anuluj</div>
                    </div>
                </div>
            </div>
        </draggable>
    </div>
    
</template>

<script>
import TaskItem from '@/components/TaskItem';
import draggable from 'vuedraggable';
export default {
    name: 'TaskList',
    components: { TaskItem, draggable },
    data() {
        return {
            currentBoard: 0,
            newTaskName: '',
            newTask: {},
            //renderComponent: true,
            boards: [
            {
                id: 0,
                name: "Realizowane",
                 addingItem: false,
            },
            {
                id: 1,
                name: "Wstrzymane",
                 addingItem: false,
            },
            {
                id: 2,
                name: "Do realizacji",
                 addingItem: false,
            },
            {
                id: 3,
                name: "Rozwiązane",
                 addingItem: false,
            },
            {
                id: 4,
                name: "Zakończone",
                 addingItem: false,
            }
            ]
            }
    },
    methods: {
        addItem() {

        },
        openNewItem(id) {
            let boardId = this.boards[id];

        boardId.active = !boardId.active
        boardId.addingItem = !boardId.addingItem;
        this.$set(this.boards, id, boardId);      
        },

        closeNewItem(id) {
        let boardId = this.boards[id];
        boardId.active = !boardId.active;
        boardId.addingItem = !boardId.addingItem;
        this.$set(this.boards, id, boardId); 
        },

        // forceRerender() {
        // this.renderComponent = false;
        
        // this.$nextTick(() => {
        //   this.renderComponent = true;
        // });
        // },

        addNewTask(id) {
            this.closeNewItem(id)
            let boardId = this.boards[id];
            let newTask = {
                id: null,
                name: this.newTaskName,
                board_id: boardId.id,
                isEditing: false,
                favourite: false
            }
            this.newTaskName = ''
            return this.newTask = newTask
            
        }
    },

}
</script>

<style lang="scss">
    .board {
        display: flex;
        width: 100%;
        height: 100vh;
        justify-content: space-between;
        .dragList {
            display: flex;
            width: 100%;
            height: 100%;
            justify-content: space-between;
        }
    }

    .taskList {
    height: auto;
    position: relative;
    display: inline-block;
    width: 17%;
    background-color: rgb(83, 87, 100);
    border-radius: 5%;
    padding: 0 15px;
    margin: 0 0 auto;
    min-height: 200px;

    .addItem {
        display: flex;
        width: 100%;
        
        background-color: transparent; 
        align-items: center;
        justify-content: center;
        .add {
            font-size: 20px;
            width: 30px;
            text-align: center;
            border: 2px solid black;
            cursor: pointer;
            margin-bottom: 5px;
        }
        .active {
            display: none;
        }

        .newItem {
            display: flex;
            width: 100%;
            flex-direction: row;
            flex-wrap: wrap;
            height: 100px;
            justify-content: space-evenly;
            input {
                width: 100%;
                height: 30px;
                transition: 0.2s linear;
                &:focus {
                    -webkit-box-shadow: 0px 0px 17px 8px rgba(21,21,128,1);
                    -moz-box-shadow: 0px 0px 17px 8px rgba(21,21,128,1);
                    box-shadow: 0px 0px 17px 8px rgba(21,21,128,1);
                }
            }
            div {
                display: flex;
                width: 100px;
                height: 40px;
                background-color: blue;
                align-items: center;
                justify-content: center;
                font-size: 20px;
                cursor: pointer;
                transition: 0.3s linear;
                &:hover {
                    background-color: rgb(15, 15, 80);
                }
            }
        }
    }
    
  }
</style>