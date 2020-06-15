<template>
  <div class="comments">
    <div class="comment-box">
      {{user.name}}
      {{comment.content}}
    </div>
  </div>
</template>

<script>
import { db } from '../main'

export default {
  props: ['cid', 'uid'],
  data () {
    return {
      comment: {},
      user: {}
    }
  },
  firestore () {
    return {
      comment: db.collection('comments').doc(this.$props.cid),
      user: db.collection('users').doc(this.$props.uid)
    }
  }
}
</script>