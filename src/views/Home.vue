<template>
  <div class="home">
    <dir class="list">
      <li v-for="company in companies" :key="company.id" class="item">
        {{company.name}}
      </li>
    </dir>
  </div>
</template>

<script>
import { db } from '../main'

export default {
  name: 'Home',
  components: {
  },
  data () {
    return {
      companies: []
    }
  },
  firestore () {
    return {
      companies: db.collection('companies')
    }
  }
}
</script>

<style lang="stylus" scoped>
.item
  list-style none
  border-top 1px solid #eee
  padding 15px 15px
  display flex
  flex-wrap no-wrap
  justify-content flex-start
  position relative
  &:first-child
    border none
  &:hover
    background rgba(0,0,0,.02)
</style>
