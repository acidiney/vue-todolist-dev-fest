<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <h1>Simples TodoList com <span>Vuejs</span></h1>
    <input type="text" placeholder="Nova tarefa" v-on:keyup.enter="addNewTask($event)">
    <table>
      <thead>
      <tr>
        <td> Role </td>
        <td> Estado </td>
        <td> Ações </td>
      </tr>
      </thead>
      <tbody>
        <tr  v-for="(item, index) in todo" v-bind:key="index">
          <td>
            <span v-bind:class="{ 'checked': item.checked }">{{ item.role }}</span>
          </td>
          <td>
            <input type="checkbox" v-model="item.checked">
          </td>
          <td>
            <button v-on:click="removeTask(index)">Eliminar</button>
          </td>
        </tr>
      </tbody>
    </table>

    <small> @DevFest2018</small>

  </div>
</template>

<script>
export default {
  name: 'app',
  data: function () {
    return {
      todo: [
          { role: 'Aprender Vue', checked: true },
          { role: 'Estudar sobre IA', checked: true },
          { role: 'Estudar sobre DL', checked: false }
      ]
    }
  },
    methods: {
      addNewTask (e) {
        this.todo.push({
            role: e.target.value,
            checked: false
        })
        e.target.value = ""
      },
        removeTask(index) {
          this.todo.splice(index, 1)
        }
    }
}
</script>

<style>
  @import url('https://fonts.googleapis.com/css?family=Abel');
  #app {
    font-weight: 100;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #333;
    margin-top: 60px;
  }

  h1 {
    font-family: 'Abel', sans-serif;
  }

  h1 > span {
    color: darkgreen;
  }

  table {
    margin: 0 auto;
    box-shadow: 1px 1px 9px #d1d1d1;

  }

  table > thead  {
    background-color: #ddd;
    font-weight: bold;
  }
  table > tbody, table > thead  {
    display: table;
  }
  table > thead > tr > td {
    padding: 5px 50px;
  }
  table > tbody > tr > td {
    padding: 5px 34px;
    text-align: left;
  }

  .checked {
    text-decoration: line-through;
  }

  input[type="text"] {
    width: 290px;
    margin-bottom: 9px;
    border: 0;
    border-bottom: 2px solid #ccc;
    background: transparent;
    padding: 10px 0;
    box-sizing: border-box;
    padding-left: 12px;
    outline: none;
    transition: .26s all ease-in-out;

  }
  input[type="text"]:focus{
    border: 2px solid darkgreen;
    transition: .26s all ease-in-out;
  }

  button {
    border: 0px;
    cursor: pointer;
    background: transparent;
    color: darkred;
  }

  button:hover {
    color: red;
  }
</style>
