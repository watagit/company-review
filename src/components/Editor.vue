<template>
  <li class="item">
    <div class="user-box">
      <div class="avatar" :style="'background-image: url('+currentUser.photoURL+')'"></div>
    </div>
    <div class="editor">
      <textarea placeholder="new comment" v-model="newComment" @keypress.enter="createComment">
      </textarea>
      <p class="message">Press Enter to Whisper</p>
    </div>
  </li>
</template>

<script>
import { db } from '../main'

export default {
  props: ['currentUser', 'currentCompany'],
  data () {
    return {
      newComment: ''
    }
  },
  methods: {
    createComment () {
      const date = new Date()
      db.collection('comments').add({
        'content': this.newComment,
        'date': date,
        'uid': this.$props.currentUser.uid,
        'cid': this.$props.currentCompany.id
      })
      .then(
        this.newComment = ''
      )
    }
  }
}
</script>