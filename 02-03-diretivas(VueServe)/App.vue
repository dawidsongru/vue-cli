<template>
    <div>
        <h1>Minha lista de tarefas!</h1>
        <button @click="() => showList = !showList">
            Ver a lista!
        </button>
        <br>    
        <input type="text" v-focus> <!-- Diretiva v-focus não existe no Vue. Iremos criá-la. -->

        <ul v-if="showList">  
            <li
                v-for="(task, index) in tasks"
                :key="`${task}-${index}`"
            >
                {{ task.name }}     <!-- Sintaze de Mustache -->
            </li>
        </ul>
        <p v-else>Lista de tarefas escondidas</p> <!-- Se estiver abaixo de um v-if, só inserir um v-else para condição contrária --> 
    </div>
</template>

<script>
const focus = {
    inserted: (el) => {// Cada propriedade que colocar dentro do objeto, vai ser uma diretiva
    el.focus()
    }
}
export default {
    directives: {
        focus
},
    data: () => ({      // Dentro do model
        showList: false,
        tasks: [        // Colocar um array de tarefas
            { name: 'Fazer o curso', isDone: false }   // Nome da tarefa: Fazer o curso
        ]
    })
}
</script>