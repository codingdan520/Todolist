<template>
  <section class="real-app">
    <input
      type="text"
      class="add-input"
      autofocus="autofocus"
      placeholder="接下去要做什么？"
      @keyup.enter="addTodo"
    >
    <Item :todo="todo" v-for="todo in filteredTodos" :key="todo.id" @del="deleteTodo"/>
    <Tabs :filter="filter" :todos="todos" @toggle="toggleFilter" @clearAllCompleted="clearAllCompleted"></Tabs>
  </section>
</template>

<script>
import Item from "./item";
import Tabs from "./tabs";
// 初始化备忘录长度
let id = 0;
export default {
  name: "Todo",
  data() {
    return {
      todos: [],
      filter: "全部"
    };
  },
  components: {
    Item,
    Tabs
  },
  computed: {
    filteredTodos() {
      if(this.filter === "全部") {
        return this.todos
      }
      const completed = this.filter === '已完成'
      return this.todos.filter(todo => completed === todo.completed)
    }
  },
  methods: {
    addTodo(e) {
      this.todos.unshift({
        id: id++,
        // 获取输入的数据(e.target.value),去掉空格((trim())
        content: e.target.value.trim(),
        completed: false
      });
      // 输入后为空
      e.target.value = "";
    },
    // 通过子组件传递过来的id删除此项
    deleteTodo(id) {
      // console.log(id);
      this.todos.splice(this.todos.findIndex(todo => todo.id === id), 1);
    },
    // 通过tabs.vue传进来state的每一项
    toggleFilter(state) {
      this.filter = state
    },
    clearAllCompleted() {
      // 使用splice删除会使列表序号错乱，所以使用过滤的方法重新显示todos的未完成项
      this.todos = this.todos.filter(todo => !todo.completed)
    }
  }
};
</script>

<style lang="stylus" scoped>
.real-app {
  width: 600px;
  margin: 0 auto;
  box-shadow: 0 0 5px #999;

  .add-input {
    position: relative;
    margin: 0;
    width: 100%;
    font-size: 24px;
    font-family: inherit;
    font-weight: inherit;
    line-height: 30px;
    outline: none;
    color: inherit;
    padding: 6px;
    border: 0;
    border-bottom: 1px solid #999;
    box-sizing: border-box;
    padding: 16px 16px 16px 60px;
  }
}
</style>

