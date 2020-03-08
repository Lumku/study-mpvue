<template>
  <div>
    <p class="card">
      {{mytext}}
      <button @click="sendInfo">msg</button>
    </p>
  </div>
</template>

<script>
export default {
  props: ['mytext'],
  methods: {
    sendInfo () {
      this.$emit('message', '来自子组件的问候')
    }
  }
}
</script>

<style>
.card {
  padding: 10px;
}
</style>
