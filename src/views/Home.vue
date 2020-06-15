<template>
  <div class="home">
    <div class="list">
      <Item
        v-for="company in companies"
        :key="company.id"
        :id="company.id"
      />
    </div>
  </div>
</template>

<script>
import { db } from '../main'
import Item from '@/components/Item.vue'

export default {
  name: 'Home',
  components: {
    Item
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
  },
  
}
</script>
