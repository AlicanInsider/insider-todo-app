<template>
  <div class="task">
  <input :value="this.title" :class="[{ notdone : this.isTodoNotDone} , {done:this.isTodoDone}]">
  <div class="button-container">
    <button v-on:click="removeTodo">Delete</button>
    <button v-on:click="doneTodo">Done</button>
    <button v-on:click="notDoneTodo">Not Done</button>
  </div> 
  </div>
</template>

<script>
export default {
  name: 'Todo',
  props: ['title', 'taskIndex'],
  methods: {
        removeTodo: function () {
            this.$emit('removeEvent', this.taskIndex);
        },
        doneTodo: function(){
          this.isTodoDone = !this.isTodoDone ;
          this.isTodoNotDone= false;
        },
        notDoneTodo: function(){
          this.isTodoNotDone = !this.isTodoNotDone;
          this.isTodoDone= false;
        }
    },
    data: function() {
      return {
        isTodoDone: false,
        isTodoNotDone: false
    }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.task{
  display:flex;
}
button{
  padding:10px;
}
.task input{
  flex:1;
  padding:10px;
}
.notdone {
  background:red;
}
.done{
  background:green;
}
</style>
