<template>
  <div id="app">
    <h1 class="ui dividing centered header">Pomodoro App</h1>
<div class="container">
<div class="row">
   <div class="col-lg-4 col-md-3 col-sm-2 col-xs-1"> </div>
  <div class="col-lg-2 col-md-3 col-sm-4 col-xs-5">
      <p class="tasks">Completed Tasks: {{todos.filter(todo => {return todo.done === true}).length}}</p>
  </div>
      <div class="col-lg-2 col-md-3 col-sm-4 col-xs-5">
    <p class="tasks">Pending Tasks: {{todos.filter(todo => {return todo.done === false}).length}}</p>
      </div>
       <div class=" col-lg-4 col-md-3 col-sm-2 col-xs-1"> </div>
</div>
</div>

<div class="container" style="text-align: center; padding: 20px 0; ">
<button type="button" class="btn btn-primary" data-toggle="modal" data-target="#exampleModal">
  Take A Break
</button>
<div class="modal fade" id="exampleModal" tabindex="-1" role="dialog" aria-labelledby="exampleModalLabel" aria-hidden="true">
  <div class="modal-dialog" role="document">
    <div class="modal-content">
      <div class="modal-header">
        <h5 class="modal-title" id="exampleModalLabel">Choose a Break!</h5>
        <button type="button" class="close" data-dismiss="modal" aria-label="Close">
          <span aria-hidden="true">&times;</span>
        </button>
      </div>
      <div class="modal-body">
        <timer2></timer2>
        <timer3></timer3>
      </div>
      <div class="modal-footer">
        <button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
      </div>
    </div>
  </div>
</div>
</div>



    <div>
      <div>
         <create-todo v-on:create-todo="createTodo"></create-todo>
<div class="ui container">
  <br>
        <todo-list v-bind:todos="todos"></todo-list>
</div>
      </div>
    </div>
  </div>
</template>

<script>
import sweetalert from 'sweetalert';
import TodoList from './components/TodoList';
import CreateTodo from './components/CreateTodo';
import timer2 from './components/timer2';
import timer3 from './components/timer3';


export default {
  name: 'app',
  components: {
    TodoList,
    CreateTodo,
    timer2,
    timer3,
  },
  data() {
    return {
      dialog: false,
      dialog2: false,
      todos: [],
    };
  },
  methods: {
    createTodo(newTodo) {
      this.todos.push(newTodo);
      sweetalert('Success!', 'To-Do created!', 'success');
    },
  },
};
</script>


<style scoped>
div.ui.card {
  display: flex;
  flex-wrap: wrap;
  margin-top: 0;
  padding-top: 0;
}

</style>