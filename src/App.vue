<template>
  <div id='app'>
    <header>
      <h1>Vue.js To Do List</h1>
      <div class='to-dos-summary'>
        <!--  pass data from main component to the ToDoList component using v-bind directive -->
        <!-- v-bind directive takes the toDos argument and binds the element's toDos attribuet to the value of the expression toDos -->
        <to-do-list v-bind:toDos='toDos'></to-do-list>
        <new-to-do v-on:add-toDo='addToDo'></new-to-do>
      </div>
    </header>
  </div>
</template>

<script>
// import the components you want to use
import sweetalert from 'sweetalert'

import ToDoList from './components/ToDoList'
import NewToDo from './components/NewToDo'

export default {
  name: 'app',
  // reference the components you want to use in the components property
  components: {
    ToDoList,
    NewToDo
  },
  // provide data to the template
  data() {
    return {
      toDos: [
        {
          title: 'wrap christmas presents',
          project: 'home',
          done: false
        },
        {
          title: 'a little life by hanya yanagihara',
          project: 'read',
          done: false
        },
        {
          title: 'learn SASS',
          project: 'learn',
          done: false
        },
        {
          title: "finish vivi's website",
          project: 'vvsundays',
          done: false
        }
      ]
    }
  }, // end data
  methods: {
    addToDo({ title, project, done }) {
      this.toDos.push({
        title,
        project,
        done
      })
      sweetalert('Added!', 'You have stuff to do!', 'success')
    }
  }
}
</script>

<style>
  header {
    margin: 30px;
    text-align: center;
  }

  h1 {
    margin: 20px 0;
  }
</style>
