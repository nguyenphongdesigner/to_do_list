<template>
  <div id="app">
    <Header />
    <Todos />
  </div>
</template>

<script>
import Header from './components/Header';
import Todos from './components/Todos.vue';
export default {
  name: 'App',
  components: { Header, Todos },
}
</script>

<style lang="scss">

</style>