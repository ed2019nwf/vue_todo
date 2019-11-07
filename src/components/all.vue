<template>
       <section class="todoapp">
            <Head @addList="addTodos"></Head>
            <ViewList :status="status" :todos="todos" @removeTodo="delItem" @changeStatus="changeStatus"></ViewList>
            <Foot @changeTab="changeTab" :todos="todos" :len="willdo"></Foot>
    </section>
</template>

<script>
import Head from "./Head";
import ViewList from "./view";
import Foot from "./Foot";
import { stat } from "fs";
import { setTimeout } from "timers";
export default {
  name: "all",
  data() {
    return {
      todos: [],
      status: 0
    };
  },
  computed: {
    willdo() {
      let willdo = this.todos.filter(val => {
        return !val.complete;
      });
      return willdo.length;
    }
  },
  methods: {
    // 添加todo
    addTodos(val) {
      if (val == "") {
        return;
      }
      this.todos.push({
        id: this.todos.length,
        content: val,
        complete: false
      });
    },
    //   删除todo
    delItem(obj) {
      this.todos = this.todos.filter(val => {
        return val.id != obj.id;
      });
    },
    changeStatus(obj) {
      if (this.todos[obj]) {
        this.$set(this.todos[obj], "complete", !this.todos[obj].complete);
        // this.todos[obj].complete = !this.todos[obj].complete;
      }
    },
    changeTab(state) {
      this.status = state;
    }
  },
  components: {
    Head,
    ViewList,
    Foot
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
