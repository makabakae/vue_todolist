<template>
  <!-- <div id="root"> -->
    <div class="todo-container">
        <div class="todo-wrap">
          <MyHeader :addTodo="addTodo"/>
          <MyList :todos="todos" :checkTodo="checkTodo" :deleteTodo="deleteTodo"/>
          <MyFooter :todos="todos" :checkAllTodo="checkAllTodo" :clearAllTodo="clearAllTodo"/>
      </div>
    </div>
 <!--  </div> -->
</template>

<script>
    import MyHeader  from './components/MyHeader.vue'
    import MyFooter from './components/MyFooter.vue'
    import MyList  from './components/MyList.vue'

    export default {
        name: 'App',
        components: {MyHeader,MyFooter,MyList},
        data(){
          return{
            todos:[

                {id:'001',title:'drinking',done:false},
                {id:'002',title:'smoking',done:false},
                {id:'003',title:'driving',done:false}
            ]
          }
        },
        methods: {
          //添加todo
          addTodo(todoObj){
          this.todos.unshift(todoObj)
          },
          //勾选或者取消勾选
           checkTodo(id){
            this.todos.forEach(todo => {
            if(todo.id === id) todo.done = !todo.done
          });
          },
           //删除一个todo
          deleteTodo(id){
            /* this.todos = this.todos.filter(
              (todo)=>{return todo.id !== id}
            ) */
            this.todos = this.todos.filter( todo => todo.id !== id)
          },
          //取消或全选todo
          checkAllTodo(done){
            this.todos.forEach((todo)=>{todo.done = done})

          },
          clearAllTodo(){
            this.todos = this.todos.filter( (todo)=>{
              return !todo.done
            })
          }
        }
      }
</script>


<style>
    /*app*/
    .todo-container {
      width: 600px;
      margin: 0 auto;
    }
    .todo-container .todo-wrap {
      padding: 10px;
      border: 1px solid #ddd;
      border-radius: 5px;
    }
</style>


