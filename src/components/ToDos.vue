<template>
  <div>
    <header>
      <h1>get it done!</h1>
    </header>
    <ul>
      <li v-for="item in toDoEntries" v-bind:key="item.id">
        <!-- die for-Schleife bezieh ihre Daten aus der App.vue -->

        <ToDoItem
          v-bind:ToDoItem="item"
          @delete-todo-event="$emit('delete-todo-event', item.id)"
        ></ToDoItem>
      </li>
    </ul>
  </div>
</template>

<script>
import ToDoItem from './ToDoItem.vue'

export default {
  name: 'ToDos',
  components: {
    ToDoItem
  },
  data () {
    return {}
  },
  props: [
    'toDoEntries' // hier sage ich der Komponente das das Array toDoEntries aus der App.vue übernommen werden soll
  ]
}
</script>

<style scope>
ul {
  padding: 2rem;
}

li {
  list-style: decimal;
  padding: 2px 5px 2px 5px;

  font-size: 1.5rem;
  color: whitesmoke;
}

li div {
  display: flex;
  justify-content: space-between;
}

li p {
  width: 100%;
  cursor: pointer;
}

@media screen and (max-width: 600px) {
  header {
    background-color: rgba(253, 221, 183, 66);
    text-align: center;
    border-radius: 0 0 10px 10px;
    -webkit-border-radius: 0 0 10px 10px;
    -moz-border-radius: 0 0 10px 10px;
    -ms-border-radius: 0 0 10px 10px;
    -o-border-radius: 0 0 10px 10px;
    border-bottom: 3px solid whitesmoke;
  }

  header h1 {
    padding-top: 2rem;
    padding-bottom: 2rem;
    color: rgba(48, 46, 46, 0.774);
    font-size: 2.5rem;
    text-shadow: 1px 1px whitesmoke;
  }
}

@media screen and (min-width: 601px) {
  header {
    background-color: rgba(253, 221, 183, 66);
    text-align: center;
    border-radius: 10px 10px 10px 10px;
    -webkit-border-radius: 10px 10px 10px 10px;
    -moz-border-radius: 10px 10px 10px 10px;
    -ms-border-radius: 10px 10px 10px 10px;
    -o-border-radius: 10px 10px 10px 10px;
    border: 2px solid whitesmoke;
  }

  header h1 {
    padding-top: 2rem;
    padding-bottom: 2rem;
    color: rgba(48, 46, 46, 0.774);
    font-size: 3.5rem;
    text-shadow: 2px 2px whitesmoke;
  }
}
</style>
