<template>
    <div class="card">
        <div class="card-header">
            <div class="card-title">Список задач</div>
            <button @click="fetchTasks">
                <refresh-icon class="icon" />
            </button>
        </div>
        <transition name="fade" mode="out-in">
            <div v-if="loading" class="tasks-loading">
                <gear-icon class="icon icon-big spin" />
            </div>
            <ul class="tasks-list" v-else>
                <tasks-list-item
                    v-for="task in tasks"
                    :key="task.id"
                    :task="task"
                    @deleted="deleteTask"
                />
            </ul>
        </transition>
        <task-creator @input="addTask" />
    </div>
</template>

<style scoped>
    .card {
        border: 1px solid #E0E0E0;
        border-radius: 4px;
        background: #FAFAFA;
        min-width: 300px;
        max-width: 100%;
    }
    .card-header {
        display: flex;
        justify-content: space-between;
        align-items: center;
        border-bottom: 1px solid #E0E0E0;
        padding: 0.75rem;
    }
    .card-title {
        font-weight: bold;
        font-size: 1.15rem;
    }
    .tasks-list {
        padding: 0;
        margin: 0;
        list-style: none;
    }
    .tasks-loading {
        display: flex;
        justify-content: center;
        padding: 0.75rem;
        border-bottom: 1px solid #E0E0E0;
    }
    .fade-enter-active, .fade-leave-active {
        transition: opacity .3s;
    }
    .fade-enter, .fade-leave-to {
        opacity: 0;
    }
</style>

<script>
import TasksListItem from './TasksListItem'
import TaskCreator from './TaskCreator'
import RefreshIcon from '../assets/refresh-icon.svg'
import GearIcon from '../assets/gear-icon.svg'
export default {
  name: 'TasksList',
  components: { TaskCreator, TasksListItem, RefreshIcon, GearIcon },
  data: () => ({
    id: 0,
    tasks: {},
    loading: true,
  }),
  created() {
    this.fetchTasks()
  },
  methods: {
    addTask(text) {
      const id = ++this.id
      this.$set(this.tasks, id, { id, text })
    },
    deleteTask(id) {
      this.$delete(this.tasks, id)
    },
    resetTasks() {
      this.tasks = {}
    },
    fetchTasks() {
      this.loading = true
      fetch('https://kodaktor.ru/j/tasklist').then(response => response.json()).then(data => {
        this.resetTasks()
        data.list.forEach(text => this.addTask(text))
        this.loading = false
      })
    },
  },
}
</script>