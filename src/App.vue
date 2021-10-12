<template>
  <div id="app">
    
      <TodoHeader/>
      <div class="todo-item">
      <StatusTodoInput 
      :todoProps="todos"
      />
    
      </div>
      <AddTodoInput @value-input="dataValue"/>
     
   
  </div>
</template>

<script>

import TodoHeader from './components/TodoList/TodoListHeader/TodoHeader.vue';
import StatusTodoInput from './components/TodoList/TodoItem/StatusTodoInput.vue';
import AddTodoInput from './components/TodoList/TodoListFooter/AddTodoInput.vue';
export default {
  name :'App',
  components : {
    TodoHeader,
    StatusTodoInput,
    AddTodoInput,

  },
  data() {
    const dataValue = (value) => {
      console.log(value);
    };
     const todos = [
        {
          title: 'Learn Vue JS',
          completed: false,
        },
        {
          title: 'Code a Todo list',
           completed: false,
        },
        {
          title: 'Học TypeScript',
           completed: false,
        }
      ];
    return {  
    dataValue,
    todos,
    }
  }
    }
</script>

<style>
#app {
  width:450px;
  height: 450px;
  background-color:#ff7675;
  top: 50%;
  left: 50%;
  position: absolute;
  transform: translate(-50% ,-50%);
  color: white;
}
* {
    margin:0;
    padding: 0;
    box-sizing: border-box;
   
    }
</style>