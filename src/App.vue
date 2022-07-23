<template>
  <div class="container">
    <h3 class="text-center">ToDo App</h3>
    <hr class="my-2" />
    <label for="todoText"></label>
    <div class="todoPart">
      <input id="todoText" type="text" placeholder="Add Something" /><button
        @click="addNewTodo"
      >
        Add
      </button>
    </div>

    <ul>
      <li
        v-for="todoItem in todoList"
        :key="todoItem.id"
        class="d-flex justify-content-between align-items-center"
      >
        <span>{{ todoItem.text }}</span>
        <button @click="deleteItem(todoItem)" class="sm red">Sil</button>
      </li>
    </ul>
    <small class="d-flex justify-content-end green"
      >You have {{ todoList.length }} todos
    </small>
  </div>
</template>

<script>
export default {
  data() {
    return {
      todoList: [],
    };
  },
  methods: {
    deleteItem(todoItem) {
      this.todoList = this.todoList.filter((t) => t != todoItem);
    },
    addNewTodo(event) {
      this.todoList.push({
        id: new Date().getTime(),
        text: event.target.value,
      });
      event.target.value = "";
    },
  },
};
</script>
