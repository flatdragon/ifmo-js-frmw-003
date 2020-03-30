<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <div>
      <a class="task-link" target="_blank" href="https://kodaktor.ru/frmw_003">Задание FRMW-003</a>
    </div>
    <tasks-list />
    <div class="author">Автор: <strong>Кочетыгов Андрей</strong></div>
  </div>
</template>

<script>
import TasksList from './components/TasksList'
export default {
  name: 'App',
  components: { TasksList },
}
</script>

<style>
  body {
    margin: 0;
    background: #ebeced;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    min-height: 100vh;
  }

  input {
    border-radius: 4px;
    border: 1px solid #eee;
    padding: 0.5rem 0.75rem;
    outline: none;
  }

  button {
    border-radius: 4px;
    border: 0;
    padding: 0.5rem 0.75rem;
    outline: none;
    color: #fff;
    background: #2c3e50;
    cursor: pointer;
  }

  input:focus {
    border-color: #4CAF50;
    box-shadow: 0 0 8px #4CAF50;
  }

  .author {
    margin-top: 0.75rem;
  }

  .task-link {
    display: inline-block;
    margin-bottom: 0.75rem;
  }

  .icon {
    display: block;
    height: 1em;
    width: 1em;
    fill: currentColor;
  }

  .icon-big {
    height: 3em;
    width: 3em;
  }

  .spin {
    animation: spin 3s infinite linear;
  }

  @-moz-keyframes spin {
    from { -moz-transform: rotate(0deg); }
    to { -moz-transform: rotate(360deg); }
  }
  @-webkit-keyframes spin {
    from { -webkit-transform: rotate(0deg); }
    to { -webkit-transform: rotate(360deg); }
  }
  @keyframes spin {
    from {transform:rotate(0deg);}
    to {transform:rotate(360deg);}
  }
</style>
