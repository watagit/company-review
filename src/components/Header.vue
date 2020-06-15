<template>
  <header>
    <router-link to="/">
      <h1>Company Review App</h1>
    </router-link>
    <div class="btns">
      <button @click="signIn">
        <p>signIn</p>
      </button>
    </div>
  </header>
</template>

<script>
import firebase from 'firebase'
import { auth } from '../main'

export default {
  methods: {
    signIn () {
      const provider = new firebase.auth.GoogleAuthProvider()
      auth.signInWithPopup(provider)
      .then((result) => {
        alert('Hello, ' + result.user.displayName + '!')
      })
    },
    signOut () {
      if (window.confirm('Are You Sure to Sign Out?')) {
        auth.signOut()
        .then(() => {
          alert('You Safely Signed Out?')
          this.$router.push('/'),
          location.reload()
        })
      }
    }
  }
}
</script>