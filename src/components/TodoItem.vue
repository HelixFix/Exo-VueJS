<template>

    <div class="todo-item" v-bind:class="{'is-complete':todo.completed}">

        <p> {{ todo.title }} </p> <!--Utilise le props todo dynamiquement pour afficher le titre -->

    </div>

</template>

<script>

export default {

    name: "TodoItem",
    props: ["todo"] // Propriétés de todo
    
}

</script>

<style scoped>

    .todo-item {

        background: #f4f4f4;
        padding: 10px;
        border-bottom: 1px #ccc dotted;

    }

    .is-complete {

        text-decoration: line-through;

    }

</style>