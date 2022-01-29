<template>
  <div class="toDoList">
    <ToDos
      v-bind:toDoEntries="toDoEntries"
      @delete-todo-event="deleteToDoItem"
    ></ToDos>
    <AddToDoButton @add-todo-event="addToDoItem"></AddToDoButton>

    <!-- Mobile:{{ mobileViewState }}
     Desktop: {{ desktopViewState }} -->
  </div>
</template>

<script>
import ToDos from './components/ToDos.vue'
import AddToDoButton from './components/AddToDoButton.vue'

export default {
  name: 'App',
  components: {
    ToDos,
    AddToDoButton
  },
  data () {
    return {
      toDoEntries: [
        { id: 1, titel: 'frühstücken', completed: false },
        {
          id: 2,
          titel: 'Fabian den Arbeitsvertrag schicken',
          completed: false
        },
        {
          id: 3,
          titel: 'motivierten Mitarbeiter einstellen der Bock auf den Job hat!',
          completed: false
        }
      ],
      mobileViewState: false,
      desktopViewState: false,
      defaultId: 0
    }
  },
  computed: {},
  methods: {
    addToDoItem (newToDoItem) {
      this.toDoEntries = [...this.toDoEntries, newToDoItem]
    },
    deleteToDoItem (toDoID) {
      this.toDoEntries = this.toDoEntries.filter(item => item.id !== toDoID)
    }
    /*handleViewPort() {
      if (window.innerWidth <= 900) {
        this.mobileViewState = true;
        this.desktopViewState = false;
        }else {
          this.mobileViewState = false;
          this.desktopViewState = true;
        }
    }*/
  },
  created () {
    // this.handleViewPort();
    // window.addEventListener("resize", this.handleViewPort)
  }
}
</script>

<style>
body {
  background-color: rgba(102, 168, 154, 66);
}

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  font-family: 'Nunito', sans-serif;
}

@import url('https://fonts.googleapis.com/css2?family=Nunito&display=swap');

@media screen and (max-width: 600px) {
  .toDoList {
    width: 95%;
    margin: auto;
  }
}

@media screen and (min-width: 601px) {
  .toDoList {
    width: 50%;
    margin: 2rem auto;
  }
}
</style>
