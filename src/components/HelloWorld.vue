<template>
  <div class="hello">
    <h1>ToDoList</h1>
    <form action ="#" @submit.prevent='addTodoList'>
    <input type="text" v-model='message'>
    <input type="submit" value="Saving it">
    </form>
    <ul>
      <li v-for="item in list" :key="item.message">
        <span>{{item.id}}、</span>
        <span>{{item.message}}</span>
        <span>{{item.time}}</span>
        <a herf="#" @click.prevent='delTodoList(item.id)'>Delete!</a>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      list: [],
      input: '',
      index: 1
    }
  },
  methods: {
    addTodoList () {
      const todo = {
        id: this.index,
        message: this.message,
        time: new Date().toLocaleTimeString()
      }
      this.list.push(todo)
      this.index++
      this.message = ''
    },
    delTodoList (id) {
      this.list = this.list.filter((item) => {
        return item.id !== id
      })
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li{
  padding: 6px;
  margin: 0;
  text-align: left;
}
a {
  color: #42b983;
}
</style>
