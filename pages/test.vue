<template>
  <div class="container">
    <input v-model="userInput" type="text" @keyup.enter="addNewTodo" />
    <mylist :props-todo-list="activeTodoList"></mylist>
    <div>
      <buttons @changeCurrentState="changeCurrentState"></buttons>
    </div>
  </div>
</template>

<script>
import mylist from '~/components/mylist.vue'
import buttons from '~/components/buttons.vue'

export default {
  components: {
    mylist,
    buttons
  },
  props: {},
  data() {
    return {
      userInput: '',
      todoList: [],
      currentState: 'active',
      isDone: false,
      insert: ''
    }
  },
  computed: {
    activeTodoList() {
      return this.todoList.filter(
        (todo) =>
          this.currentState === 'all' || todo.state === this.currentState
      )
    }
  },
  methods: {
    // changeCurrentState(state) {
    //   this.currentState = state
    // }
    addNewTodo() {
      this.todoList.push({
        label: this.userInput,
        state: 'active'
      })
      this.userInput = ''
      alert('목록에 추가 되었습니다.')
    },
    changeCurrentState(data) {
      this.currentState = data
    }
    // toggleTodoState(todo) {
    //   if (todo.state === 'active') {
    //     todo.state = 'done'
    //     alert('할 일을 완료하였습니다.')
    //   } else {
    //     todo.state = 'active'
    //     alert('완료 취소 되어 목록에 다시 추가합니다.')
    //   }
    // }
  }
}
</script>

<style></style>
