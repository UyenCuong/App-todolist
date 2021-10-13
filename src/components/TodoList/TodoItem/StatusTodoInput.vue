<template>
<div class="todoItem " >
   <ul class="todoItem__list" v-for="(todo , index) in todos "
      :key="todo.id"
      :title="todo.title"
     
      @remove="todos.splice(index, 1)"
    >
        <li class="todoItem__list--title ">
          {{ index + 1 }} .
          <p :class="{ 'is-completed': todo.completed }">{{todo.title}}</p>
            <input 
            class="todoItem__list--input " 
            type="checkbox" 
            :checked="todo.completed"
            v-on:change="markItemCompleted"
            />
            
        
          <DeleteTodoButton @remove="removeFunction" />
      
        </li>
  </ul>
  
</div>
 <div class="todoItem__move--item">
          <p>{{ move }}</p>
          <input 
            type="checkbox" 
            class="toggle-action">
            </div>
</template>

<script>
import { computed } from 'vue';
import DeleteTodoButton from './DeleteTodoButton.vue';
export default {
     name:'StatusTodoInput',
    props :['todoProps'],
     components: {
       DeleteTodoButton,
     },
    
     data(props) {
       const todos = computed(() => props.todoProps);
       console.log(todos.value);
       const markItemCompleted = () => {
         console.log('mark')
       }
       const removeFunction = (index) =>{
        todos.value.splice(index, 1);
       }
       
    return {
      todos,
      markItemCompleted,
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