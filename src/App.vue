<template>
  <div id="app">
    <Header/>
    <AddTask/>
    <Tasks/>
  </div>
</template>

<script>
import Header from './components/header/Header'
import AddTask from './components/addtask/AddTask'
import Tasks from './components/tasks/Tasks'
export default {
  name: 'App',
  components: {
    Header,
    AddTask,
    Tasks
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 0;
}

body{
    margin: 0px;
}

</style>
