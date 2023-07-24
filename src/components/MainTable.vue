<template>
    <table>
      <tr>
        <th><h1>ID<arrow-elem /></h1></th>
        <th><h1>Заголовок<arrow-elem /></h1></th>
        <th><h1>Описание<arrow-elem /></h1></th>
      </tr>
      <tr v-for="array in localArray" :key="array.id">
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
      localArray: [
  {
    "userId": 1,
    "id": 1,
    "title": "sunt aut facere repellat provident occaecati excepturi optio reprehenderit",
    "body": "quia et suscipit\nsuscipit recusandae consequuntur expedita et cum\nreprehenderit molestiae ut ut quas totam\nnostrum rerum est autem sunt rem eveniet architecto"
  },
  {
    "userId": 1,
    "id": 2,
    "title": "qui est esse",
    "body": "est rerum tempore vitae\nsequi sint nihil reprehenderit dolor beatae ea dolores neque\nfugiat blanditiis voluptate porro vel nihil molestiae ut reiciendis\nqui aperiam non debitis possimus qui neque nisi nulla"
  },
  {
    "userId": 1,
    "id": 3,
    "title": "ea molestias quasi exercitationem repellat qui ipsa sit aut",
    "body": "et iusto sed quo iure\nvoluptatem occaecati omnis eligendi aut ad\nvoluptatem doloribus vel accusantium quis pariatur\nmolestiae porro eius odio et labore et velit aut"
  },
  {
    "userId": 1,
    "id": 4,
    "title": "eum et est occaecati",
    "body": "ullam et saepe reiciendis voluptatem adipisci\nsit amet autem assumenda provident rerum culpa\nquis hic commodi nesciunt rem tenetur doloremque ipsam iure\nquis sunt voluptatem rerum illo velit"
  },
  {
    "userId": 1,
    "id": 5,
    "title": "nesciunt quas odio",
    "body": "repudiandae veniam quaerat sunt sed\nalias aut fugiat sit autem sed est\nvoluptatem omnis possimus esse voluptatibus quis\nest aut tenetur dolor neque"
  },
  {
    "userId": 1,
    "id": 6,
    "title": "dolorem eum magni eos aperiam quia",
    "body": "ut aspernatur corporis harum nihil quis provident sequi\nmollitia nobis aliquid molestiae\nperspiciatis et ea nemo ab reprehenderit accusantium quas\nvoluptate dolores velit et doloremque molestiae"
  },
  {
    "userId": 1,
    "id": 7,
    "title": "magnam facilis autem",
    "body": "dolore placeat quibusdam ea quo vitae\nmagni quis enim qui quis quo nemo aut saepe\nquidem repellat excepturi ut quia\nsunt ut sequi eos ea sed quas"
  },
  {
    "userId": 1,
    "id": 8,
    "title": "dolorem dolore est ipsam",
    "body": "dignissimos aperiam dolorem qui eum\nfacilis quibusdam animi sint suscipit qui sint possimus cum\nquaerat magni maiores excepturi\nipsam ut commodi dolor voluptatum modi aut vitae"
  }]
    }
  }
}
</script>

<style scoped lang="scss">
@import '../assets/main.scss';
table{
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
