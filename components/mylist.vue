<template>
  <div class="mylist">
    <p>helloVue</p>
    <template v-for="(todo, idx) in propsTodoList">
      <button
        :key="idx"
        class="static"
        :class="[todo.state === 'active' ? 'blueBtn' : 'redBtn']"
        @click="toggleTodoState(todo)"
      >
        {{ todo.label }}
      </button>
    </template>
  </div>
</template>

<script>
export default {
  props: {
    propsTodoList: {
      type: Array,
      default: () => []
    },
    propsTest: {
      type: String,
      default: ''
    }
  },
  methods: {
    toggleTodoState(todo) {
      console.log('todo', todo)
      if (todo.state === 'active') {
        todo.state = 'done'
        alert('할 일을 완료하였습니다.', todo.state)
      } else {
        todo.state = 'active'
        alert('완료 취소 되어 목록에 다시 추가합니다.', todo.state)
      }
    }
  }
}
</script>

<style>
.redBtn {
  background: coral;
}
.blueBtn {
  background: skyblue;
}
</style>
