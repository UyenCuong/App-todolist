<template>
<div class="todoItem " >
   <ul class="todoItem__list" v-for="(todo , index) in todos "
      :key="index"
      :title="todo.title"
     
      @remove="todos.splice(index, 1)"
    >
        <li class="todoItem__list--title ">
          {{ index + 1 }} .
          <p :class="{ 'is-completed': todo.completed }" @click="markItemCompleted(todo)">{{todo.title}}</p>
            <input 
            class="todoItem__list--input " 
            type="checkbox" 
            :checked="todo.completed"
            v-on:change="markItemCompleted(todo)"
            />
            
        
          <DeleteTodoButton @remove="removeFunction(index)" />
      
        </li>
  </ul>
  
</div>
 <div class="todoItem__move--item">
    <p>{{ move }}</p>
    <input 
      v-model="sortEnable"
      type="checkbox" 
      class="toggle-action"
      @click="sortListTodo"
      >
  </div>
</template>

<script>
import { ref, computed, watchEffect, watch } from 'vue';
import DeleteTodoButton from './DeleteTodoButton.vue';
export default {
     name:'StatusTodoInput',
    props :['todoProps'],
     components: {
       DeleteTodoButton,
     },
    
     data(props) {
       const sortEnable = ref(false);
       const todos = computed(() => props.todoProps);
       const markItemCompleted = (todo) => {
         todo.completed = !todo.completed;
       }

       const sortListTodo = () => {
        for(let index = 0; index < todos.value.length - 1; index++) {
          for(let indexFake = index + 1; indexFake <  todos.value.length; indexFake++) {
             if(todos.value[index].completed) {
               let memory = todos.value[index];
               todos.value[index] = todos.value[indexFake]; 
               todos.value[indexFake] = memory;
            }
          }
        }
       }
       
       const removeFunction = (index) =>{
        todos.value.splice(index, 1);
       }
       watchEffect(() => {
        todos.value.splice(0, 1);
       });
       watch(props.todoProps, ()=>{
         if(sortEnable.value) {
           console.log(123);
           sortListTodo();
         }
       });
    return {
      todos,
      sortEnable,
      markItemCompleted,
      sortListTodo,
      removeFunction,
      move : 'Move done item at the end?',
      
    }
  },
 }
</script>

<style>
.todoItem {
  margin-top:30px;
  overflow: auto;
 max-width: 450px;
 max-height: 200px;
}
.todoItem__list {
  list-style-type: none;
  margin: 0;
  padding: 0;
  
}
.todoItem__list--title {
   background-color: rgba(255, 255, 255, 0.2);
    margin-bottom: 4px;
    line-height: 50px;
    display: flex;
		justify-content: space-between;
		align-items: center;
    padding: 0 35px;
    
}
.todoItem__list--input {
    margin-left: auto;
}
.todoItem__move--item {
   margin: 0 25px;
    display: flex;
    align-items: center;
    justify-content: right;
}
.todoItem__move--item .toggle-action {
    width:40px;
    height:20px;
    -webkit-appearance: none;
    background-color: #c6c6c6;
    position: relative;
    border-radius: 10px;
}
.todoItem__move--item input[type="checkbox"]::after {
  content: "";
    position: absolute;
    width:20px;
    height:20px;
    top: 0;
    left: 0;
    background-color: #fff;
    border-radius: 50%;
}
.todoItem__move--item input:checked[type="checkbox"] {
   background-color: #f0abab;
}
.todoItem__move--item input:checked[type="checkbox"]::after {
    left: 20px;
    background-color: #e7e7e7;
}
.is-completed {
  text-decoration: line-through;
} 
</style>