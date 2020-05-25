<template>
  <div class="container">
    <button type="button" @click="changeCurrentState('active')">할 일</button>
    <button type="button" @click="changeCurrentState('done')">완료</button>
    <button type="button" @click="changeCurrentState('all')">전체</button>
  </div>
</template>

<script>
export default {
  methods: {
    changeCurrentState(state) {
      this.$emit('changeCurrentState', state)
    }
  }
}
</script>

<style></style>
