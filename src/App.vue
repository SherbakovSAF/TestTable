<template>
  <div class="container">
    <MainSearch />
    <MainTable />
  </div>
</template>

<script>
import MainSearch from './components/MainSearch.vue'
import MainTable from './components/MainTable.vue';

export default {
  name: 'App',
  components: {
    MainSearch,
    MainTable
  }
}
</script>

<style>
body {
  font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
}
.container {
  max-width: 1077px;
  margin: 0 auto;
}
</style>
