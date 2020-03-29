<template>
    <div class="taskItem">
        <h1>{{taskList.name}}</h1>
    </div>
</template>

<script>
export default {
    props: {
        name: String
    },
    data() {
        return{
            taskList: [
                {
                    id: 1,
                    name: "Poprawa edito"
                },
                {
                    id: 2,
                    name: "Testowy"
                }
            ]
        }
    }
}
</script>

<style>
    .taskItem {
        position: relative;
        width: 100%;
        border: 2px solid black;
        height: 100px;
    }
</style>