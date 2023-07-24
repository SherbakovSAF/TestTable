<template>
  <div class="pagination__panel">
    <button id="prevBtn" @click="selectPage--" :disabled="selectPage <= 1">Назад</button>
    <div class="page__wrap">
      <button @click="selectPage = page" v-for="page in calPage" :key="page"
      :class="{
        activePage: selectPage == page
      }">
        {{ page }}
      </button>
    </div>
    <button id="nextBtn" @click="selectPage++" :disabled="selectPage >= 10">Вперёд</button>
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

@import '../assets/main.scss';
.pagination__panel {
  justify-content: space-between;
  display: grid;
  grid-template-columns: repeat(3, auto);



  .page__wrap {
    button {
      padding: 0 7px;
      font-style: italic;
      
    }
  }
  button{
    background: none;
    border: none;
    cursor: pointer;
    user-select: none;
    width: auto;
    color: $mainColor;
  }

  .activePage{
    color: #7EBC3C;
  }

  button:disabled{
    opacity: 0.3;
  }

  #prevBtn, #nextBtn {
    padding: 0px 45px;
  }
}
</style>
