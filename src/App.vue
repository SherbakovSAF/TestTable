<template>
  <div class="container">
    <MainSearch v-model="searchViaTitle"/>
    <div v-show="amountPosts > 0">
      <MainTable 
      @amountElem="setAmountPosts" 
      :selectedPage="page"
      :amountItemForPage="amountItemForPage"
      :filterTitle="searchViaTitle"
    />
    <pagination-panel 
      :postsLength="amountPosts" 
      @selectedPage="setSelectedPage"
      :amountItemForPage="amountItemForPage"
    />
    </div>
    <date-null  v-show="amountPosts < 1"/>
    <!-- Какая то проблема с Vue, почему v-if и v-else не работает корректно -->
  </div>
</template>

<script>
import MainSearch from './components/MainSearch.vue'
import MainTable from './components/MainTable.vue';
import PaginationPanel from './components/PaginationPanel.vue';
import DateNull from './components/DateNull.vue'

export default {
  name: 'App',
  components: {
    MainSearch,
    MainTable,
    PaginationPanel,
    DateNull,
  },
  data(){
    return {
      amountPosts: null,
      page: 1,
      amountItemForPage: 10,
      searchViaTitle: '',
    }
  },
  methods: {
    setAmountPosts(posts){
      this.amountPosts = posts
    },
    setSelectedPage(page){
      this.page = page
    }
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