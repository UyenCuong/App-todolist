<template>
 <button @click="deleteItem">Delete</button>

 
</template>

<script>
export default {
    name: "DeleteTodoButton",
   props: ['title'],
  
    data(){
     const deleteItem =() =>{
         this.$emit('remove');
     }
        return {
            deleteItem,
         
        }
    }
}
</script>

<style>

</style>