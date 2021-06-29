<template>
    <div>
        <h1>Minha lista de tarefas!</h1>
        <button @click="handleShowHideList">
            Ver a lista!
        </button>
        <br>
        <input
            type="text"
            @keyup.enter="addTask"
            v-focus
            v-model="currentTask"> <!-- Diretiva v-focus não existe no Vue. Iremos criá-la. -->

        <ul v-if="showList">
            <li
                v-for="(task, index) in tasks"
                @dblclick="complete(task)"
                :key="`${task}-${index}`"
                class="task-item"
                :class="{
                    'line-through': task.isDone
                }"
            >
                {{ task.name }}
                <button
                    @click="remove(task)">   <!-- @ é atalho para v-on: --> <!-- Sempre que tiver evento, usa @ -->
                &times;</button>
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
        currentTask: "",
        showList: false,
        tasks: [        // Colocar um array de tarefas
            { name: 'Fazer o curso', isDone: false }   // Nome da tarefa: Fazer o curso
        ]
    }),
    methods: {
        handleShowHideList () {
            this.showList = !this.showList
        },
        addTask () {
            this.tasks.push({
                name: this.currentTask,
                isDone: false
            })
            this.currentTask = ''
        },
        complete (task) {
            this.tasks = this.tasks.map(t => {
                if (t.name === task.name) {
                    return { ...t, isDone: !t.isDone }
                }
                return { ...t }
            }) 
        },
        remove (task) {
            this.tasks = this.tasks.filter(t => t.name !== task.name)
        }
    }
}
</script>

<style scoped>
.line-through {
    text-decoration: line-through;
}
.task-item{
    cursor: pointer;
}
</style>