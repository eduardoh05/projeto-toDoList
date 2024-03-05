<template>
    <v-text-field label="Add Task"
        v-model="task.title"
        @keyup.enter="addTask">
    </v-text-field>

    <list-tasks :tasks="tasks"/>
</template>

<script setup>
    import ListTask from '../components/ListTasks.vue'

    import {ref} from 'vue'

const tasks = ref([
    {
    title: "Estudar Vue",
    description: "Estudar Vue com Vuetify"
    },
    {
        title: "Ler documentação",
        description: "Ler a documentação do Vuetify"
    }
]);

const addTask = ()=> {
    tasks.value.push({
        title: task.value.title,
        description: task.value.description
    })
    task.value = {
        title: "",
        description:""
    }
};

const task = ref({
    title: "",
    description: ""
});
</script>

<style>

</style>