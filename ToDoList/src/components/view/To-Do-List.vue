<script setup>
import { ref } from 'vue'
const tasks = ref([])
function addTask() {
    const taskText = prompt('Digite a tarefa: ')
    if (taskText) {
        tasks.value.push({ id: Date.now(), text: taskText})
    }
}
function removeTask(id){
    tasks.value = tasks.value.filter(task => task.id !== id)
}
</script>

<template>
    <h1>Lista de Tarefas</h1>
    <div class="addTask">
        <button class="buttonHeader" @click="addTask">Adicionar Tarefa</button>
    </div>
    <div>
        <ul>
            <li v-for="task in tasks" :key="task.id">
                {{ task.text }}
                <button @click="removeTask(task.id)">Remover</button>
            </li>
        </ul>
    </div>
</template>

<style scoped>
.buttonHeader{
    background-color: gray;
    border-radius: 5px;
    margin: 5px;
}

.buttonHeader:hover{
    transition: transform 0.2s ease background-color 0.2s ease;
    background-color: blue;
    font-size: 16px;
}

</style>