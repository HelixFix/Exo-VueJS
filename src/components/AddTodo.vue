<template>

    <div>

        <form @submit="addTodo">

            <input type="text" v-model="title" name="title" placeholder="Add"> <!-- v-model pour créer une liaison de données bidirectionnelle sur les champs de formulaire (input, select ou textarea). -->
            <input type="submit" value="Submit" class="btn">

        </form>

    </div>

</template>

<script>

import uuid from 'uuid'; // Importer le generateur d'ID
export default {

    name: "AddTodo",
    data() {
        return {
            title: ''
        }
    },
    methods: {
        addTodo(e) {
            e.preventDefault(); // On ne veut pas que le form submit à un fichier
            const newTodo = {
                // id: uuid.v4(), ne marche pas
                id: uuid, // Utiliser uuid, inutile si on utilise axios
                title: this.title,
                completed: false
            }
            // Send up to parent
            this.$emit('add-todo', newTodo);
            this.title = ''; // Vide le champ après l'envoi
        }
    }

}

</script>

<style scoped>

    form {

        display: flex;

    }

    input[type="text"] {
        flex: 10;
        padding: 5px;
    }

    input[type="submit"] {
        flex: 2;
    }

</style>