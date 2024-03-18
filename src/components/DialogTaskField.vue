<template>
  <div class="text-center pa-4">
    <v-dialog
      v-model="props.dialog"
      persistent
      min-width="400"
      max-width="600"
    >

      <v-card>
      <v-card-title class="text-h5">Edit Task</v-card-title>
        <v-text-field label="Title" class="pr-5 pl-5" v-model="props.task.title"></v-text-field>
        <v-text-field label="Description" class="pr-5 pl-5" v-model="props.task.description"></v-text-field>
        <template v-slot:actions>
          <v-spacer></v-spacer>

          <v-btn color="green-darken-1"
          @click="$emit('toggle')">
            Ok
          </v-btn>
        </template>
      </v-card>
    </v-dialog>
  </div>
</template>

<script setup>
import { ref, defineProps } from 'vue';

const props = defineProps({
    dialog: Boolean,
    task: Object
})

</script>