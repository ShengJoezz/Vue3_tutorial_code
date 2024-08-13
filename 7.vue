<template>
<form @submit.prevent="submitToDo">
<input v-model="newToDo" placeholder="Type Here">
<button>Add ToDo</button>
</form>
<ul>
   <li v-for="todo in toDoList">
    {{ todo.text }}
    <button @click="removeToDo">X</button>
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
  toDoList.value.push(NewToDo.value)
  NewToDo.value=''
}
function removeToDo(todo){
    toDoList.value=toDoList.value.filter((t)=> t !== todo.id)
}
</script>