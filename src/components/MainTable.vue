<template>
    <table>
      <tr>
        <th><h1>ID<arrow-elem /></h1></th>
        <th><h1>Заголовок<arrow-elem /></h1></th>
        <th><h1>Описание<arrow-elem /></h1></th>
      </tr>
      <tr v-for="array in posts" :key="array.id">
        <td>{{ array.id }}</td>
        <td>{{ array.title }}</td>
        <td>{{ array.body }}</td>
      </tr>
    </table>
</template>

<script>
import ArrowElem from '../components/svgElements/ArrowElem'

export default {
  name: 'MainTable',
  components: {
    ArrowElem
  },
  data(){
    return {
      posts: []
    }
  },
  async mounted(){
    const res = await fetch('https://jsonplaceholder.typicode.com/posts')
    const newArray = await res.json()
    this.posts = [...newArray]
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
</style>
