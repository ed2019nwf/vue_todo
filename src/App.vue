<template>
  <div id="app">
    <All></All>
  </div>
</template>

<script>

export default {
  name: 'App',
  components:{
    All:resolve=>{
      require(['@/components/all'],resolve);
    }
  }
}
</script>

<style>
</style>
