<template>
  <div class="todo-footer" v-show="total" >
        <label>
         <!--  <input type="checkbox" :checked="isAll" @change="checkAll"/> -->
          <input type="checkbox" v-model="isAll"/>
        </label>
        <span>
          <span>已完成{{doneTodo}}</span> / 全部{{total}}
        </span>
        <button class="btn btn-danger" @click="clearAll" >清除已完成任务</button>
      </div>
</template>
<script>
//import { set } from 'vue/types/umd'
    export default {
      name: 'MyFooter',
      props:['todos','checkAllTodo','clearAllTodo'],
      computed:{
        total(){

          return this.todos.length
        },
        //计算总共完成了多少，使用reduce方法。
        doneTodo(){
          /*   const x = this.todos.reduce((pre,current)=>{
              return pre + (current.done ? 1:0)
            },0) */
              return this.todos.reduce(  (pre,todo)=> pre + (todo.done ? 1:0),0    )
        },
        isAll:{
          get(){
              return this.total === this.doneTodo && this.total >0
          },
          set(value){
                this.checkAllTodo(value)
          }
          
        }
              
      },
      methods:{
        clearAll(){
          this.clearAllTodo()
        }   
      }
      
 }
</script>
<style>
    /*footer*/
      .todo-footer {
        height: 40px;
        line-height: 40px;
        padding-left: 6px;
        margin-top: 5px;
      }
      .todo-footer label {
        display: inline-block;
        margin-right: 20px;
        cursor: pointer;
      }
      .todo-footer label input {
        position: relative;
        top: -1px;
        vertical-align: middle;
        margin-right: 5px;
      }
      .todo-footer button {
        float: right;
        margin-top: 5px;
      }
</style>


