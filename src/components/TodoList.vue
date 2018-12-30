<template>
    <div class="todoList">
      <div class="todoItem" v-for="(todoitem,index) in list" :key="index">
        <span>{{todoitem.name}}</span>
      </div>
    </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';

@Component({
  props:{
    list:Array,
  },
  components: {
  },
})
export default class TodoList extends Vue{
}
</script>
