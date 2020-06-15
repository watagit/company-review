<template>
  <div class="item">
    <div class="company-box">
      <router-link :to="'/company/'+company.id">
        <div class="company-name">{{company.name}}</div>
      </router-link>
    </div>
  </div>
</template>

<script>
import { db } from '../main'

export default {
  props: ['id'],
  data () {
    return {
      company: {}
    }
  },
  firestore () {
    return {
      company: db.collection('companies').doc(this.$props.id)
    }
  }
}
</script>

<style lang="stylus">
.item
  list-style none
  border-top 1px solid #eee
  padding 15px 15px
  display flex
  flex-wrap no-wrap
  justify-content flex-start
  position relative
  .editor
    position relative
    width 100%
    textarea
      background transparent
      resize none
      height 80px
      width 96%
      border none
      padding 10px 2%
      font-size .9rem
      font-weight lighter
      &:focus
        outline none
    .message
      opacity 0  
      position absolute
      bottom 5px
      right 10px
      transition .2s
      font-size .8rem
    &:hover
      .message
        opacity 1
</style>