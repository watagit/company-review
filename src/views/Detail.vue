<template>
  <div>
    <div class="company-name">
      会社名：{{company.name}}
    </div>
    <div class="company-description">
      説明：{{company.description}}
    </div>
  </div>
</template>

<script>
import { db } from '../main'

export default {
  data () {
    return {
      company: {}
    }
  },
  firestore () {
    return {
      company: db.collection('companies').doc(this.$route.params.id)
    }
  }
}
</script>
