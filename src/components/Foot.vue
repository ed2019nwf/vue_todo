<template>
    <footer class="footer" v-if="todos.length">
        <span class="todo-count"><strong>{{len}}</strong>项待处理</span>
        <ul class="filters">
            <li class="selected">
                <a href="javascript:void(0)" @click="()=>{this.$emit('changeTab',0)}">全部</a>
            </li>
            <li>
                <a href="javascript:void(0)" @click="()=>{this.$emit('changeTab',1)}">未完成</a>
            </li>
            <li>
                <a href="javascript:void(0)" @click="()=>{this.$emit('changeTab',2)}">已完成</a>
            </li>
        </ul>
    </footer>
</template>

<script>
export default {
  props:['todos','len'],
  data() {
    return {};
  },
  methods: {}
};
</script>

<style scoped>
</style>