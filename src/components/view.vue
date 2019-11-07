<template>
    <section class="main">
        <input id="toggle-all" class="toggle-all" type="checkbox">
        <ul class="todo-list">
            <li v-for="(todo,index) in list" :class="{completed:todo.complete}" @click="changeStatus(index)">
                <div class="view">
                    <input class="toggle" type="checkbox" v-model="todo.complete">
                    <label>{{todo.content}}</label>
                    <button class="destroy" @click.stop="removeTodo(todo)"></button>
                </div>
            </li>
        </ul>
    </section>
</template>

<script>
export default {
  props: ["todos", "status"],
  data() {
    return {
      list: []
    };
  },
  mounted() {},
  watch: {
    status: {
      handler(val) {
        this.puclicFun(val);
      },
      immediate: true
    },
    todos: {
      handler() {
        this.puclicFun(this.status);
      },
      deep:true
    }
    // status(val, oldval) {
    //   if (val == 0) {
    //     this.list = this.todos;
    //   } else if (val == 1) {
    //     this.list = this.todos.filter(todo => {
    //       return !todo.complete;
    //     });
    //   } else {
    //     this.list = this.todos.filter(todo => {
    //       return todo.complete;
    //     });
    //   }
    // },
  },
  computed: {},
  methods: {
    puclicFun(val) {
      if (val === 0) {
        this.list = this.todos;
      } else if (val === 1) {
        this.list = this.todos.filter(todo => {
          return !todo.complete;
        });
      } else {
        this.list = this.todos.filter(todo => {
          return todo.complete;
        });
      }
    },
    removeTodo(index) {
      this.$emit("removeTodo", index);
    },
    changeStatus(obj) {
      this.$emit("changeStatus", obj);
    }
  }
};
</script>

<style scoped>
</style>