<script setup lang="ts">
import HelloWorld from './components/HelloWorld.vue'
import { ref, type Ref } from 'vue'

const message = ref('')
const todos: Ref<string[]> = ref([])
const addTodo = (inputValue: string) => {
  todos.value.push(inputValue)
  message.value = ''
}
</script>

<template>
  <header>
    <div class="wrapper">
      <HelloWorld msg="TODO LIST" />
    </div>
  </header>
  <div>
    <p>{{ message }}</p>
    <input type="text" v-model="message" />
    <button @click="addTodo(message)">추가</button>
  </div>
  <h2>my todo list</h2>
  <p v-if="todos.length === 0">todo list가 없습니다.</p>
  <ul v-else>
    <li v-for="todo in todos" v-bind:key="todo">{{ todo }}</li>
  </ul>
</template>

<style scoped>
header {
  line-height: 1.5;
  max-height: 100vh;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}
</style>
