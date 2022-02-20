<template>
  <div id="app">
    <div class="index">
      <h2>Список дел</h2>
    <input type="text" v-model="newText" placeholder="Введите дело...">
    <button @click="textPush">Добавить</button>
    <todoList :persons = persons :isDone = isDone :i = i :isTodoDelete = isTodoDelete />
    <hr>
    <p>Всего дел: {{ persons.length }}</p>
    <router-view/>
    </div>
  </div>
</template>

<script>
import todoList from '@/components/todoList'

export default {
  name: 'app',
  data () {
    return {
      persons: [],
      newText: '',
      i: 1,
      isDone: false,
      isDelete: false
    }
  },

  methods: {
    textPush () {
      if (this.newText !== '') {
        this.newText = this.newText[0][0].toUpperCase() + this.newText.substr(1, this.newText.length)
        this.persons.push({
          id: this.persons.length + 1,
          text: this.newText,
          isComplete: this.isDone,
          isTodoDelete: this.isDelete
        })
        this.newText = ''
        this.i = this.i + 1
      }
    }
  },
  components: {
    todoList
  }
}
</script>

<style>
li {
  list-style-type: decimal;
}
.index {
  background-color: #e2ffe0;
  width: 30%;
  border: 1px solid black;
  text-align: center;
  min-height: 500px;
}
</style>
