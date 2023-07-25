<template>
    <div>
      <pre-loader v-if="!posts.length"/>
      <table v-else>
        <tr>
          <th @click="sortEl('plus', 'minus', 'id', 'typeSortID')">
            <h1>ID
              <arrow-elem :class="{'svgNeg': typeSortID == 'minus'}"/>
            </h1>
          </th>
          <th @click="sortEl('ABC', 'CBA', 'title', 'typeSortTitle')">
            <h1>Заголовок
              <arrow-elem :class="{'svgNeg': typeSortTitle == 'CBA'}"/>
            </h1>
          </th>
          <th @click="sortEl('ABC', 'CBA', 'body', 'typeSortBody')">
            <h1>Описание
              <arrow-elem :class="{'svgNeg': typeSortBody == 'CBA'}"/>
            </h1>
          </th>
        </tr>
        <tr v-for="array in filterPostsPagination" :key="array.id">
          <td>{{ array.id }}</td>
          <td>{{ array.title }}</td>
          <td>{{ array.body }}</td>
        </tr>
      </table>
    </div>
</template>

<script>
import ArrowElem from '../components/svgElements/ArrowElem'
import PreLoader from './svgElements/PreLoader.vue'

export default {
  name: 'MainTable',
  components: {
    ArrowElem,
    PreLoader
  },
  props: {
    selectedPage: {
      type: Number,
      required: true
    },
    amountItemForPage: {
      type: Number,
      required: true
    },
    filterTitle: {
      type: String,
      required: false
    }
  },
  data(){
    return {
      posts: [],
      typeSortID: 'plus',
      typeSortTitle: 'ABC',
      typeSortBody: 'ABC',
    }
  },
  computed: {
    filterPostsPagination(){
      return this.filterPostsSearch.slice(this.selectedPage * this.amountItemForPage - this.amountItemForPage, this.selectedPage * this.amountItemForPage)
    },
    filterPostsSearch(){
      return this.posts
        .filter(e=> e.title.toLowerCase()
        .includes(this.filterTitle.toLowerCase()))
    },
  },
  methods: {
    sortEl(positiveStr, negativeStr, key, variable ){
      if(this[variable] === positiveStr){
        this.post = this.posts.sort((a,b)=> a[key] < b[key] ? 1 : -1)
        this[variable] = negativeStr
      } else {
        this.post = this.posts.sort((a,b)=> a[key] > b[key] ? 1 : -1)
        this[variable] = positiveStr
      }
    },
  },
  async mounted(){
    this.$emit('isPreloared', true)
    const res = await fetch('https://jsonplaceholder.typicode.com/posts')
    const newArray = await res.json()
    this.posts = [...newArray]
    this.$emit('isPreloared', false)
  },
  watch: {
    filterPostsSearch(){
      this.$emit('amountElem', this.filterPostsSearch.length)
    }
  }
}
</script>

<style scoped lang="scss">
@import '../assets/main.scss';
table{
  margin: 15px 0px;
  border-collapse: collapse;
  tr {
    
    th {
      padding: 19px 23px 16px 23px;
      background-color: $mainColor;
      border: 1px solid $mainColor;
      cursor: pointer;

      h1{
        display: flex;
        align-items: center;
        justify-content: center;

        color: white;
        font-weight: 600;
        font-size: 14px;
      }

      svg{
        height: 7px;
        width: 12px;
        rotate: 0deg;
        margin-left: 25px;
        transition: rotate .15s ease-in;
      }

      .svgNeg{
        rotate: 180deg;
      }
    }
    td {
      border: 1px solid #E3E6EC;
      color: $mainColor;
      font-size: 13px;
      font-weight: 500;
      padding: 15px 11px;
      &:first-child {
        text-align: center;
      }
    }
  }
}
@import '../assets/mainMedia';
</style>
