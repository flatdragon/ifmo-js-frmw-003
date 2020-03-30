<template>
    <li class="tasks-list-item">
        <label class="tasks-list-item-checkbox" title="Пометить задачу как выполненную">
            <input type="checkbox" @change="deleteTask">
        </label>
        <label class="tasks-list-item-text">{{ task.text }}</label>
    </li>
</template>

<style scoped>
    .tasks-list-item {
        display: flex;
        align-items: center;
        text-align: left;
        border-bottom: 1px solid #E0E0E0;
    }
    .tasks-list-item-checkbox {
        padding: 0.75rem;
        border-right: 1px solid #E0E0E0;
        cursor: pointer;
    }
    .tasks-list-item-checkbox > input {
        cursor: pointer;
    }
    .tasks-list-item-text {
        flex-grow: 1;
        padding: 0.75rem;
    }
</style>

<script>
export default {
  name: 'TasksListItem',
  props: {
    task: {
      type: Object,
      default() {
        return {}
      },
    },
  },
  methods: {
    deleteTask() {
      this.$emit('deleted', this.task.id)
    },
  },
}
</script>