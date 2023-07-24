<template>
  <div class="pagination__panel">
    <button @click="selectPage--" v-show="selectPage > 1">Назад</button>
    <div>
      <button @click="selectPage = page" v-for="page in calPage" :key="page">{{ page }}</button>
    </div>
    <button  @click="selectPage++" v-show="selectPage < 10">Вперёд</button>
  </div>
</template>

<script>
export default {
  name: 'PaginationPanel',
  props: {
    postsLength: {
      type: Number,
      required: false,
    },
    amountItemForPage: {
      type: Number,
      required: true
    }
  },
  data(){
    return {
      selectPage: 1
    }
  },
  methods: {
    selectedPage(page) {
      this.selectPage = page
    },
  },
  computed: {
    calPage() {
      let localArray = []
      for(let i = 1; i <= this.postsLength / this.amountItemForPage; i++){
        localArray.push(i)
      }
      return localArray
    }
  },
  watch: {
    selectPage(){
      this.$emit('selectedPage', this.selectPage)
    }
  }
  
}
</script>

<style scoped lang="scss">
.pagination__panel {
  display: flex;
}
</style>
