<template>
  <div class="main__search">
    <div>
      <input type="text" placeholder="Поиск" :value="modelValue" @input="$emit('update:modelValue', $event.target.value)">
      <search-elem />
    </div>
  </div>
</template>

<script>
import SearchElem from './svgElements/SearchElem.vue'
export default {
  name: 'MainSearch',
  components: {
    SearchElem
  },
  props: {
    modelValue: String 
  },
  emits: ['update:modelValue']
}
</script>

<style scoped lang="scss">
.main__search {
  background-color: #5A5C66;
  width: 630px;

  div {
    display: flex;
    align-items: center;
    padding: 16px 25px;
      input {
      background-color: inherit;
      width: 100%;
      font-size: 14px;
      line-height: 0;
      border: none;
      color: #B2B7BF;
      outline: none;
      &::placeholder {
        color: inherit;
      }
    }
  }
  
}


</style>
