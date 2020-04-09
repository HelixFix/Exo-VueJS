<template>

<div>

    <div v-bind:key="todo.id" v-for="todo in todos"> <!-- Boucle table ID Todo -->
        <!-- <h3> {{ todo.title }} </h3> Affiche le titre de chaques éléments -->
        <TodoItem v-bind:todo="todo"/> <!-- Afficher TodoItem -->

    </div>

</div>
    
</template>

<script>
import TodoItem from './TodoItem.vue' // Importer TodoItem

export default {
    name: "Todos",
    components: {
        TodoItem // Utiliser TodoItem
    },
    props: ["todos"] // Propriétés de todos
}

</script>

<style scoped>



</style>