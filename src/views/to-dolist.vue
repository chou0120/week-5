<template>
   <div class="to-dolist">
       <h1>This is a To-Do List</h1>
      <todoform @newtodo="addtodo">
          <h2 slot="title">Add a ToDo Task</h2>
          <p slot="desc">this will add your todoList</p>
      </todoform>
       <todo :todos= "todolist" @removetodo="appDeletetodo" />
   </div>
</template>
<script>
import todo from "@/components/todo.vue";
import todoform from "@/components/todoform.vue";
import axios from "axios";

export default {
    data(){
        return{
            todolist:["walk the dog","go for a ride"] 
        };
    },
    components:{
todo,
todoform
    }, 
    methods: {
        appDeletetodo(index) {
            this.todolist.splice(index, 1);
             axios
             .put("https://chou0120-vue-and-axios.firebaseio.com/data.json", this.todolist)
             .then(response => {
                 console.log("your data was deleted status: " + response.status);
             })
             .catch(error =>{
                 console.log(error);
             });
         },
         addtodo(todo ){
             this.todolist.push(todo);
             axios
             .put("https://chou0120-vue-and-axios.firebaseio.com/data.json", this.todolist)
             .then(response => {
                 console.log("your data was saved status: " + response.status);
             })
             .catch(error =>{
                 console.log(error);
             });

}
    }
}
</script>

<style scoped>
ul{
    list-style:none;
    margin:0 auto;
    width:50%;
}
ul li{
    border-bottom:1 px solid #acacac;
    padding: 10px 0;
    margin-bottom:10px;
}
</style>