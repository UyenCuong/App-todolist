<template>
  <div id="app">
    
      <TodoHeader/>
      <div class="todo-item">
      <StatusTodoInput/>
    
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
    }
    return {  
    dataValue,
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