<template>
<div class="task-item" >
    <h3>{{task.title}}</h3>
    <p>{{task.description}}</p>
    <div>
    <a @click="deleteTask"> <img src="https://www.svgrepo.com/show/292083/delete-cancel.svg" alt="delete"> </a>
    <a @click="editTaskItem"> <img src="https://www.svgrepo.com/show/391838/file-edit-alt.svg" alt="Edit"> </a>
    <a v-if="(isComplete!==true)" @click="completeTask" class="complete-task"> <img src="https://www.svgrepo.com/show/402906/white-heavy-check-mark.svg" alt="Edit"> </a>
    <a v-if="(isComplete===true)" @click="completeTask"  class="complete-task"> <img src="https://www.svgrepo.com/show/247755/left-arrow-back.svg" alt="Edit"> </a>
    
   
   </div>
    <div class="edit-task-item" v-show="editTask">
        <input  class="edit-task-item-child" type="text" placeholder="Edit Title" v-model="title" />
        <input class="edit-task-item-child" type="text" placeholder="Edit Description" v-model="description">
        <button class="edit-task-item-child" @click="changeTask">Edit</button>
    </div>
    <p>{{task.inserted_at}}</p>
</div>
</template>

<script setup>
import { ref } from 'vue';
import { useTaskStore } from '../stores/task';
import { supabase } from '../supabase';

const taskStore = useTaskStore();
const emit = defineEmits(["deleteTasksHijo", "editTask","completeTask"])

const editTask = ref(false)
const isComplete = ref(props.task.is_complete)



const description = ref()
const title=ref()


const props = defineProps({
    task: Object,
});


const deleteTask = async () => {
    console.log(props.task);
    await taskStore.deleteTask(props.task.id);
    emit ("deleteTasksHijo")
};
const editTaskItem =  () => {
    editTask.value = !editTask.value
    
}
const changeTask = async () => {
 console.log(description, title);
    await  taskStore.changeTask(title.value, description.value, props.task.id);
    editTask.value = false;
    
  emit ("editTask")
};






const completeTask = async () => {
    
 
    await taskStore.completeTask(isComplete.value, props.task.id)
    isComplete.value = !isComplete.value;
    emit ("completeTask")
}



</script>

<style></style>

<!--
**Hints**
1. ref() or reactive() can be used here to store the following, think if you want to store them either individually or
like an object, up to you.

2. Data properties need here are the following: a boolean to store a false**Important variable, a string to store an error,
a string to store the value of the task that the user can edit, an initial false boolean to hide the inputFIeld used to edit
the new task detail or details[this is in reference of the task title and the task description].

3. Store the custom emit events that will be used to call the functions of the homeView for editing, deleting and toggling the
status[completed, not complted] of the taskItem.

4. Function to handle the error with the data properties used to control the error and the the boolean controlling the boolean
empty variable.

5. Function to handle the edit dialogue where the inputField is displayed and the string used to store the value of the
inputField will be used here to save the value as a prop on this function.

6. Function to emmit a custom event emit() that takes 2 parameters a name for the custom event and the value that will be
send via the prop to the parent component. This function can control the toggle completion of the task on the homeview.

7. Function to edit the task information that you decided that the user can edit. This function's body takes in a conditional
that first checks if the value of the task [either title and description or just title] is empty which if true it runs the
function used to handle the error on hint4. Else, the conditional sets the first mentioned boolean data property on hint2
back to its inital boolean value to hide the error message and repeat the same for the data property mentioned 4th on hint2;
a constant that stores an object that holds the oldValue from the prop item and the value of the task coming from the data
property mentioned 3rd on hint2; a custom event emit() that takes 2 parameters a name for the custom event and the value
from the object used on this part of the conditional and lastly this part of the conditional sets the value of input field
to an empty string to clear it from the ui.

8. Function to emmit a custom event emit() that takes 2 parameters a name for the custom event and the value that will be
send via the prop to the parent component. This function can control the removal of  the task on the homeview.
-->
