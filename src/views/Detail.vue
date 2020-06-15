<template>
  <div class="detail">
    <div class="company-name">
      会社名：{{company.name}}
    </div>
    <div class="company-description">
      説明：{{company.description}}
    </div>
    <CommentList
      v-for="comment in myComments"
      :key="comment.id"
      :cid="comment.id"
      :uid="comment.uid"
    />
    <Editor :currentUser="currentUser" :currentCompany="company" />
  </div>
</template>

<script>
import { db } from '../main'
import { auth } from '../main'
import firebase from 'firebase'
import Vue2Filters from 'vue2-filters'
import Editor from '@/components/Editor'
import CommentList from '@/components/CommentList'

export default {
  components: {
    Editor,
    CommentList
  },
  data () {
    return {
      company: {},
      currentUser: {},
      myComments: []
    }
  },
  created () {
    auth.onAuthStateChanged(user => {
      this.currentUser = user
    })
  },
  firestore () {
    return {
      company: db.collection('companies').doc(this.$route.params.id),
      myComments: db.collection('comments').where('cid', '==', this.$route.params.id)
    }
  }
}
</script>

<style lang="stylus" scoped>
.detail
  font-size 20px
  .company-name
    margin-bottom 5px
</style>
