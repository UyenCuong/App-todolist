<template>
<div class="todoFooter">
    <p>
   {{ add }}
  </p>
  <form class="todoFooter--add" @submit.prevent="addTodo()">
       <input v-model="nameTitle" type="text" class="todoFooter--add__input" name="nameTitle">
       <AddTodoButton />
  </form>
</div>
  
 
</template>

<script>
import { ref } from 'vue';
import AddTodoButton from './AddTodoButton.vue';
export default {
 name:'AddTodoInput',
  components: {
       AddTodoButton,
     },
 data (){
     const add ='Add to the todo list';
     const nameTitle = ref('');
     const addTodo = () => {
         this.$emit('value-input', nameTitle.value);
         nameTitle.value = '';
     }
     return{
        add,
        nameTitle,
        addTodo,
     }
 }
}
</script>

<style>
.todoFooter {
    padding : 0 35px;
}
.todoFooter--add {
    display:flex;
    justify-content: space-between;
     
   
}
.todoFooter--add__input {
    outline: none;
    padding:8px;
    font-size:0.93rem;;
    border: none;
    border-radius: 2px;
    cursor:auto;
    width: 256px;
}
</style>