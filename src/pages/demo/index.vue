<template>
  <div>demo
    <Card mytext="hellon card" @message="getChild"></Card>
  </div>
</template>
 
<script>
import Card from '../../components/card.vue'
export default {
  components: {
    Card
  },
  data () {
    return {}
  },
  methods: {
    getChild (data) {
      console.log(data)
    }
  },
  beforeCreate () {
    console.log('beforeCreate')
  },
  created () {
    console.log('create')
  },
  onload () {
    console.log('load')
  },
  onReady () {
    console.log('ready')
  },
  onHide () {
    console.log('hide')
  },
  onShow () {
    console.log('show')
  }
}
</script>

<style scoped>
</style>
