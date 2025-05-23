<script setup>
import {ref, watch} from "vue";
import vueMounted from './VueMounted.vue'
let id = 0;

const message = ref('hello world');
const dynamicId = ref('dynamicId');
const count = ref(0);
const text = ref('');
const awesome = ref(true);
const newTodo = ref('');
const hideCompleted = ref(false);
const watchCount = ref(0);
const todos = ref([
  {
    id: id++,
    text: 'learn html',
    done: true
  },
  {
    id: id++,
    text: 'learn css',
    done: true
  },
  {
    id: id++,
    text: 'learn vue',
    done: true
  }
])

function increment() {
  count.value++;
}

function inputText(e) {
  text.value = e.target.value;
}

function toggle() {
  awesome.value = !awesome.value;
}

function addTodo() {
  todos.value.push({id: id++, text: newTodo.value});
  newTodo.value = '';
}

function removeTodo(rTd) {
  todos.value = todos.value.filter((e) => e !== rTd);
}
</script>

<template>
  <div>{{message}}</div>
  <br>
  <div :id="dynamicId">{{dynamicId}}</div>
  <br>
  <input type="text" :value="text" @input="inputText"> <!-- 입력값 -->
  <br>
  <p>{{ text }}</p> <!-- 표출값 -->
  <br>
  <button @click="increment">count value : {{count}}</button>
  <br>

  <!--https://vuejs.org/tutorial/#step-6-->
  <button @click="toggle">Toggle</button>
  <h1 v-if="awesome">if</h1>
  <h1 v-else="awesome">else</h1>
  <br>

  <!--https://vuejs.org/tutorial/#step-7-->
  <form @submit.prevent="addTodo">
    <input v-model="newTodo" required>
    <button>add todo</button>
  </form>
  <ul>
    <li v-for="todo in todos" :key="todo.id">
      <input type="checkbox" v-model="todo.done">
      <span :class="{done: todo.done}">{{ todo.text }}</span>
      <button @click="removeTodo(todo)">X</button>
    </li>
  </ul>
  <button @click="hideCompleted = !hideCompleted">
    {{ hideCompleted ? 'Show all' : 'Hide completed' }}
  </button>
  <a href="VueMounted.vue"></a>
</template>

<style scoped>
#dynamicId {
  color: red
}
.done {
  text-decoration: line-through;
}
</style>
