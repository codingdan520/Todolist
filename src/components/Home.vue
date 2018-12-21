<template>
  <div class="todolist">
    <Header></Header>
    <Todo></Todo>
    <Footer></Footer>
  </div>
</template>

<script>
import Header from './Todo/header'
import Footer from './Todo/footer'
import Todo from './Todo/todo'

export default {
  name: "Home",
  components: {
    Header,
    Footer,
    Todo
  }
};
</script>

<style lang="stylus" scoped>
.todolist {
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  background: url('../../static/imgs/1.jpg') no-repeat;
  background-size: cover;
  background-position: center;
  opacity: 0.8;
  z-index: -1;
  background-color: #999;
}
</style>

