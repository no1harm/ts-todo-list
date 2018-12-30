<template>
  <div id="app">
    <NewTodo @addTodo="addTodo"/>
    <TodoList :list="list" @updateTodo="updateTodo" @deletedTodo="deleteTodo"/>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import TodoList from './components/TodoList.vue';
import NewTodo from './components/NewTodo.vue';
import Todo from './model/Todo';

@Component({
  components: {
    NewTodo,TodoList
  },
  watch:{
    list(newValue){
      localStorage.setItem('data',JSON.stringify(newValue))
    }
  }
})
export default class App extends Vue {
  list:Array<Todo> = localStorage.getItem('data') ? JSON.parse(localStorage.getItem('data')) : [];
  addTodo(name:string){
    let todo:Todo = {name:name,status:'todo'}
    this.list.push(todo)
  };
  updateTodo(todo:Todo,part:Partial<Todo>){
    let index:number = this.list.indexOf(todo)
    let newTodo:Todo = Object.assign({},todo,part)
    this.list.splice(index,1,newTodo)
  }
  deleteTodo(todo:Todo){
    let index:number = this.list.indexOf(todo)
    this.list.splice(index,1)
  }
}
</script>

<style scoped lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
