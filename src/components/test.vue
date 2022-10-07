<template>
  <h1>{{firstName}}</h1>
  <p>{{car}}</p>
  <button @click="onClick">click me</button>
</template>

<script>
import { ref,reactive  } from 'vue'
export default {
    name:'thanh-ff',
    setup(){
        const firstName=ref("quang thanh dep trai")
        const car = reactive({
            price:1000,
            name:"mazda"
        })
        function onClick(){
            console.log(car)
        }
        return {firstName,onClick}
    }
}
</script>

<style>

</style>