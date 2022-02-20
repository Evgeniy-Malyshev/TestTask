<template>
    <div>
      <ul>
      <li v-for="persons in persons" :key="persons.i">
        <span :class="{isShow: persons.isComplete}" > {{persons.text}}<input type="checkbox" class="check" v-model="persons.isComplete"></span>
        <button class="button__delete" @click="addDelete(persons)">x</button>
      </li>
    </ul>
    </div>
</template>

<script>

export default {
  props: ['persons', 'isDone', 'isDelete', 'i'],
  components: {
  },
  methods: {
    addDelete (persons) {
      this.persons.splice(this.persons.indexOf(persons), 1)
    }
  }
}
</script>

<style>
li {
  text-align: left;
  margin-left: 5%;
}
.isShow{
  text-decoration: line-through;
  color: rgb(94, 93, 93);
}
.button__delete{
  border-radius: 50%;
  background-color: rgb(250, 95, 95);
  font-style: bold;
  border: 0.4px solid rgb(54, 54, 54);
}
</style>
