<template>
    <div class="task-creator">
        <label class="task-creator-input">
            <input type="text" v-model="text" @keydown.enter="create">
        </label>
        <button class="task-creator-button" title="Создать задачу" @click="create">
            <plus-icon class="icon" />
        </button>
    </div>
</template>

<style>
    .task-creator {
        display: flex;
        padding: 0.75rem;
    }
    .task-creator-input {
        display: flex;
        flex-grow: 1;
        margin-right: 0.75rem;
    }
    .task-creator-input > input {
        width: 100%;
    }
</style>

<script>
import PlusIcon from '../assets/plus-icon.svg'
export default {
  name: 'TaskCreator',
  components: { PlusIcon },
  data: () => ({
    text: '',
  }),
  methods: {
    create() {
      if (this.text === '') return
      this.$emit('input', this.text)
      this.reset()
    },
    reset() {
      this.text = ''
    },
  },
}
</script>