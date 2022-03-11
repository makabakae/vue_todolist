<template>
  <ul class="todo-main">
    <MyItem 
      v-for="todoObj in todos" 
      :key="todoObj.id" 
      :todo="todoObj" 
      :checkTodo="checkTodo" 
      :deleteTodo="deleteTodo"
    />
    
  </ul>
</template>

<script>
    import MyItem from './MyItem.vue'
    export default {
      name: 'MyList',
      components: {MyItem},
      props:['todos','checkTodo','deleteTodo']
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
    /*main*/
  .todo-main {
    margin-left: 0px;
    border: 1px solid #ddd;
    border-radius: 2px;
    padding: 0px;
  }

</style>
