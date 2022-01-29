<template>
  <div class="listenElement" v-bind:class="{ completed: ToDoItem.completed }">
    <p @click="markComplete">{{ ToDoItem.titel }}</p>

    <font-awesome-icon
      class="icon"
      icon="trash-alt"
      @click="$emit('delete-todo-event', ToDoItem.id)"
    />
  </div>
</template>

<script>
export default {
  name: 'ToDoItem',
  components: {},
  data () {
    return {}
  },
  methods: {
    markComplete () {
      this.ToDoItem.completed = !this.ToDoItem.completed
    }
  },
  props: ['ToDoItem']
}
</script>

<style scope>
.completed {
  text-decoration: line-through;

  text-decoration-color: rgba(204, 199, 191, 0.836);
}
.listenElement .icon {
  color: rgba(204, 199, 191, 0.836);
}
</style>
