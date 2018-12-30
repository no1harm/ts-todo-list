<template>
  <div class="new-todo">
    <input type="text" v-model="text">
    <button @click="addTodo">添加</button>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';

@Component
export default class NewTodo extends Vue {
  text = '';
  addTodo(){
    this.$emit('addTodo',this.text)
    this.text = ''
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

</style>
