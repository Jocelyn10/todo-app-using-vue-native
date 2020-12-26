<template>
  <view class="container">
    <!-- StatusBar is a native component -->
    <status-bar background-color="blue" bar-style="light-content" />
    <Header title="Todo App" />

    <view class="inputContainer">
      <text-input class="input" v-model="newTodoText" />
      <touchable-opacity class="add-btn" :on-press="newTodo">
        <text class="btn-text">ADD</text>
      </touchable-opacity>
    </view>
    <view class="todo" v-for="todo in todos" :key="todo.id">
      <touchable-opacity :on-press="() => toggleDone(todo.id)">
        <text class="todo-text done" v-if="todo.done">{{ todo.title }}</text>
        <text class="todo-text" v-else>{{ todo.title }}</text>
      </touchable-opacity>
      <touchable-opacity
        class="remove-btn"
        :on-press="() => removeTodo(todo.id)"
      >
        <text class="remove-btn-text">Remove</text>
      </touchable-opacity>
    </view>
  </view>
</template>

<script>
import Header from "./components/Header";
export default {
  components: {
    Header,
  },
  data() {
    return {
      newTodoText: "",
      todos: [
        {
          id: 0,
          title: "Go shopping",
          done: false,
        },
        {
          id: 0,
          title: "Hey shopping",
          done: false,
        },
      ],
    };
  },
  methods: {
    newTodo() {
      this.todos.push({
        id: this.todos.length + 1,
        title: this.newTodoText,
        done: false,
      });

      this.newTodoText = "";
    },
    toggleDone() {},
    removeTodo() {},
  },
};
</script>
<style>
.container {
  background-color: white;
  flex: 1;
}
.inputContainer {
  flex-direction: row;
  justify-content: center;
  align-content: center;
}
.input {
  flex: 1;
  height: 35px;
  background-color: #f3f3f3;
  font-size: 18px;
  color: #888888;
}
.add-btn {
  width: 100px;
  height: 35px;
  background-color: #ffc808;
  justify-content: center;
  align-items: center;
}
.btn-text {
  font-size: 18px;
  font-weight: 700;
}
.todo {
  flex-direction: row;
  justify-content: space-between;
  padding: 15px;
}
.todo-text {
  font-size: 18px;
}
.done {
  color: #aaaaaa;
}
.remove-btn-text {
  font-size: 18px;
  color: red;
}
</style>
