<template>
    <div class="todoList">
      <div class="todoItem" v-for="(todoitem,index) in list" :key="index">
        <input type="checkbox" :checked="todoitem.status === 'done'"
        @change="changeStatus(todoitem,$event)">
        <span>{{todoitem.name}}</span>
        <span @click="deleteTodo(todoitem)">删除</span>
      </div>
    </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import Todo from '../model/Todo';

@Component({
  props:{
    list:Array,
  },
  components: {
  },
})
export default class TodoList extends Vue{
  changeStatus(todoitem:Todo,e:Event){
    let checked = (<HTMLInputElement>e.target).checked
    this.$emit('updateTodo',todoitem,{status:checked?'done':'todo'})
  }
  deleteTodo(todoitem){
    this.$emit('deletedTodo',todoitem)
  }
}
</script>
