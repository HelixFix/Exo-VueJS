<template>

<div>

    <div v-bind:key="todo.id" v-for="todo in todos"> <!-- Boucle table ID Todo -->
        <h3> {{ todo.title }} </h3> <!-- Affiche le titre de chaques éléments -->

    </div>

</div>
    
</template>

<script>

export default {
    name: "Todos",
    props: ["todos"]
}

</script>

<style scoped>



</style>