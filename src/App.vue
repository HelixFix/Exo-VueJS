<template>

    <div id="app">

        <!-- <Todos />  Afficher Todos -->

        <!-- v-bind permet de faire des liaisons -->
      <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/> <!-- Methods deleteTodo -->

    </div>

</template>

<script>

import Todos from './components/Todos'; // importer Todos

export default {

  name: 'App',
  components: {
      Todos // Utiliser Todos
  },

  data () {

      return {
// Like a fake REST API
          todos: [
              {
                  id: 1,
                  title: "Todo One",
                  completed: false
              },
              {
                  id: 2,
                  title: "Todo Two",
                  completed: true
              },
              {
                  id: 3,
                  title: "Todo Three",
                  completed: false
              }
          ]
      }
  },

  methods: {
      deleteTodo(id) {
          this.todos = this.todos.filter(todo => todo.id !== id); // Le filtre boucle comme un foreach avec une condition qui permet de retourner un tableau baser sur cette condition et cette condition est qu'on veut tout sauf l'ID supprimer
      }
  }

}

</script>

<style>

    * {
        box-sizing: border-box;
        margin: 0;
        padding: 0;
    }

    body {
        font-family: Arial, Helvetica, sans-serif;
        line-height: 1.4;
    }

</style>
