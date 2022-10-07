<template>
  <div class="abc">
    <Hoaquangthanhabcd/>
    <Test/>
  </div>
  <Todos/>
</template>

<script>
import Hoaquangthanhabcd from "./components/HelloWorld.vue"
import Todos from "./components/Todo.vue"
import Test from "./components/test.vue"
export default {
  name: 'App',
  data(){
    return {
      count:0,
    }
  },
  components:{ Hoaquangthanhabcd, Todos,Test }
}
</script>

<style>
  .abc{
    background: #ccc;
    color: black;
    text-align: center;

  }

</style>
