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
