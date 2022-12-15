
   <template>
 <div class="new-task">
    <h1>Add a new Task</h1>
    <div v-if="showErrorMessage">
        <p class="error-text">{{ errorMessage }}</p>
    </div>
    <div  class="input-container">
        <div class="input-field">
            <input type="text" placeholder="Add a Task Title" v-model="title">
        </div>
        <div class="input-field">
            <input type="text" placeholder="Add a Task Description " v-model="description">
        </div>
        <div>
         <button @click="addTask" class="button-add">Add</button>   
        </div>
    </div>
    
    </div>
</template>

<script setup>
import { ref } from "vue";
import { useTaskStore } from "../stores/task"   
import Swal from 'sweetalert2'

const taskStore = useTaskStore();

const emit = defineEmits(["getTaskHijo"])

// variables para los valors de los inputs
const title = ref('');
const description = ref('');

// constant to save a variable that holds an initial false boolean value for the errorMessage container that is conditionally displayed depending if the input field is empty
const showErrorMessage = ref(false);

// const constant to save a variable that holds the value of the error message
const errorMessage = ref(null);

// Arrow function para crear tareas.
const addTask = async () => {
if(title.value.length === 0 || description.value.length === 0){
    // Primero comprobamos que ningún campo del input esté vacío y lanzamos el error con un timeout para informar al user.

    showErrorMessage.value = true;
    errorMessage.value =  Swal.fire({
  title: 'Error!',
  text: 'You have to add a task title with the description',
  icon: 'error',
  confirmButtonText: 'Ok'
});
    setTimeout(() => {
       
    showErrorMessage.value = false;
    }, 10);

} else {
    // Aquí mandamos los valores a la store para crear la nueva Task. Esta parte de la función tenéis que refactorizarla para que funcione con emit y el addTask del store se llame desde Home.vue.

    await taskStore.addTask(title.value, description.value);
    title.value = '';
    description.value = '';
    emit ("getTaskHijo");
}
};

</script>

<style>


@media (max-width: 760px) {
.input-field input {
padding: 1rem 4rem;
 }
}

@media (max-width: 350px) {
.input-field input {
padding: 1rem 3rem;
    }
}
</style>
