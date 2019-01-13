<template>
  <div class="task">
  <div class="task-container">
    <input placeholder="Task name" type="text" v-model="title" class="task-container-input">
    <button v-on:click="addTask">Click Me</button>
       <div v-for="(todo,index) in todos">
        <Todo v-bind:title="todo.title" v-on:removeEvent="removeTodo" v-bind:taskIndex="index"></Todo>
       </div>
  </div>
  </div>
</template>

<script>
import Todo from './Todo.vue'

export default {
  name: 'Todolist',
  components: {
    Todo
  },
  data: function() {
      return {
          title:'',
          todos: [{
            title: 'Todo A'
        }, {
            title: 'Todo B'
        }, {
            title: 'Todo C'
        }, {
            title: 'Todo D'
        }],
      }
  },
  methods: {
        addTask:function(){
            if(this.title.length > 0){
                this.todos.push({title:this.title});
            }
            
            this.title = '';
        },
        removeTodo: function(index) {
            this.todos.splice(index, 1);
        }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.task-container{
    width:500px;
    height:500px;
    position:absolute;
    top:50%;
    left:50%;
    transform:translate(-50%,-50%);
}
.task-container-input{
    width:99.2%;
}
button{
    width:100%;
}
</style>
