<template>

    <div id="app">

        <Header />
        <AddTodo v-on:add-todo="addTodo"/> <!-- Utiliser AddTodo-->

        <!-- <Todos />  Afficher Todos -->

        <!-- v-bind permet de faire des liaisons -->
        <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/> <!-- Methods deleteTodo -->

    </div>

</template>

<script>

import Header from './components/layout/Header'; // importer Header.vue
import Todos from './components/Todos'; // importer Todos.vue
import AddTodo from './components/AddTodo'; // importer AddTodo.vue
import axios from 'axios'; // Importer/définir axios

export default {

  name: 'App',
  components: {
      Header, // Enregistrer Header
      Todos, // Enregistrer Todos
      AddTodo // Enregistrer AddTodo
  },

  data () {

      return {
// Like a fake REST API
          todos: [
            //   {
            //       id: 1,
            //       title: "Todo One",
            //       completed: false
            //   },
            //   {
            //       id: 2,
            //       title: "Todo Two",
            //       completed: true
            //   },
            //   {
            //       id: 3,
            //       title: "Todo Three",
            //       completed: false
            //   }
          ]
      }
  },

  methods: {

        deleteTodo(id) {
            this.todos = this.todos.filter(todo => todo.id !== id); // Le filtre boucle comme un foreach avec une condition qui permet de retourner un tableau baser sur cette condition et cette condition est qu'on veut tout sauf l'ID supprimer
        },

        addTodo(newTodo) { // Ajoute un nouveau todo dans le tableau

            const { title, completed } = newTodo;
            axios.post('https://jsonplaceholder.typicode.com/todos', {
                title,
                completed
            })
            
            .then(res => this.todos = [...this.todos, newTodo, res.data])
            .catch(err => console.log(err));
            
        }

    },
    created() {
        axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
        .then(res => this.todos = res.data) // Réponse
        .catch(err => console.log(err)); // débug
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

    .btn {
        display: inline-block;
        border: none;
        background: #555;
        color: #fff;
        padding: 7px 20 px;
        cursor: pointer;
    }

    .btn:hover {
        background: #666;
    }

</style>
