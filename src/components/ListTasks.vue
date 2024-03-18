<template>
    <v-container>
    
        <v-list lines="three" select-strategy="classic">
            <v-list-subheader>General</v-list-subheader>

            <v-list-item 
            v-for="(task, index) in props.tasks" 
            :key="index"
            :value="index">
                <template v-slot:prepend="{ isActive }">

                <v-list-item-action start>
                    <v-checkbox-btn :model-value="isActive"></v-checkbox-btn>
                </v-list-item-action>
                </template>

                <v-list-item-title>{{task.title}}</v-list-item-title>

                <v-list-item-subtitle>
                {{task.description}}
                </v-list-item-subtitle>

                <template v-slot:append>
                    <v-menu>
                        <template v-slot:activator="{ props }">
                            <v-btn
                            color="grey-lighten"
                            icon="mdi-dots-vertical"
                            variant="text"
                            v-bind="props"
                            >

                            </v-btn>
                        </template>
                        <v-list>
                            <v-list-item value="1" @click="toggleEdit(index)">
                                <v-list-item-title>Editar</v-list-item-title>
                            </v-list-item>
                            <v-list-item value="2" @click="toggleDelete(index)">
                                <v-list-item-title>Excluir</v-list-item-title>
                            </v-list-item>
                        </v-list>
                    </v-menu>
                </template>
            </v-list-item>
            </v-list>

            <dialog-task-field 
            :dialog="showDialogTaskField"
            :task="tasks[indexTaskSelect]"
            @toggle="toggleEdit"/>

            <dialog-delete 
            :dialog="showDialogTaskField"
            @toggleDelete="toggleDelete"/>
    </v-container>

</template>

<script setup>
import {defineProps} from 'vue';
import DialogTaskField from '@/components/DialogTaskField.vue'
import DialogDelete from '@/components/DialogDelete.vue'

const props = defineProps({
    tasks: Object,
})

const indexTaskSelect = ref(0);
const showDialogTaskField = ref(false);
const toggleEdit = (index) =>{
    showDialogTaskField.value = !showDialogTaskField.value;
    if (index != null)
        indexTaskSelect.value = index;
}

const toggleDelete = (index) =>{
    showDialogTaskField.value = !showDialogTaskField.value;
    if (index != null)
        indexTaskSelect.value = index;
}

const showDialogDelete = ref(false);

</script>

<style>

</style>