<template>
  <div>
    <div class="error">
      <p>{{ error }}</p>
    </div>
    <div class="addToDoButton">
      <form autocomplete="off" @submit="addToDo">
        <input
          type="text"
          v-model="titel"
          name="titel"
          placeholder=" Was machen wir?"
        />
        <button type="submit">
          <font-awesome-icon class="icon" icon="plus" />
        </button>
      </form>
    </div>
  </div>
</template>

<script>
import { v4 as uuidv4 } from 'uuid'

export default {
  name: 'AddToDoButton',
  components: {},
  data () {
    return {
      titel: '',
      id: null,
      error: ''
    }
  },
  computed: {},
  methods: {
    addToDo (event) {
      event.preventDefault()

      if (this.titel === '') {
        return (this.error = 'Aufgabe nicht vergessen!')
      } else {
        const newToDoObject = {
          id: uuidv4(),
          titel: this.titel,
          completed: false
        }
        this.$emit('add-todo-event', newToDoObject)
        this.titel = ''
        this.error = null
      }
    }
  },
  props: ['AddToDoButton']
}
</script>

<style scope>
input:focus {
  outline: none;
}

.addToDoButton {
  display: flex;
  justify-content: center;
  margin-bottom: 1rem;
}

.addToDoButton .icon {
  color: rgba(48, 46, 46, 0.774);
  font-size: 1.5rem;
}

form {
  display: flex;
  width: 100%;
  justify-content: center;
}
input[type='text'] {
  width: 70%;
  font-size: 1.5rem;
}

input::placeholder {
  font-size: 1.5rem;
}

form button {
  background-color: rgba(0, 0, 0, 0);
  border: none;
  margin-left: 1rem;
  display: flex;
  place-items: center;
}

.error p {
  text-align: center;
  color: whitesmoke;
  font-size: 1.5rem;
}
</style>
