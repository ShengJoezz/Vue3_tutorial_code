<template>
    <form @submit.prevent="submitToDo">
    <input v-model="NewToDo" placeholder="Type Here">
    <button>Add ToDo</button>
    </form>
    <ul>
       <li v-for="todo in toDoList">
        <span :class=“done”>{{todo.text}} </span>
        <button @click="removeToDo(todo)">X</button>
       </li>    
    </ul>
    </template>
    <script setup>
    import {ref} from 'vue'
    const id =ref(0)
    const toDoList =ref(
        [ {id:id.value,text:"study Vue",done:true},
          {id:++id.value,text:"study Cesium",done:true},
          {id:++id.value,text:"study OpenFoam",done:true}
        ]
    )
    const NewToDo=ref("")
    function submitToDo(){
      toDoList.value.push({id:++id.value,text:NewToDo.value,done:false})
      NewToDo.value=''
    }
    function removeToDo(todo){
        toDoList.value=toDoList.value.filter((t)=> t.id !== todo.id)
    }
    </script>
<style>
.done{
  text-decoration: line-through;
}
</style>