<template>
 <header class="header">
     <h1>{{ title }}</h1>
     <p>
         {{ target }}
     </p>
 </header>
</template>

<script>

export default {
    name : 'TodoHeader',
    data(){
    return {
        title : "Todo List",
        target: ' Get thing done, one item at a time.',
    }
    }
};
</script>

<style >
.header {
    font-weight: 300;
    margin:35px 35px 0 35px;
    position: relative;
}
.header ::after {
    content: "";
    position: absolute;
    top: 60px;
    left: 0;
    width: 100%;
    height: 1px;
    background-color: #fff;
}
</style>