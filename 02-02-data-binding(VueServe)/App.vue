<template>
    <div>
        <h1 :style="{ textDecoration: decoration }">Hello {{ name }}!</h1> <!-- Sintaxe de Mustashe, aspas duplas {{ }} --> <!-- textDecoration como CSS inline --> <!-- v-bind é o mesmo que : --> <!-- v-bind ou apenas : interpreta como JavaScript -->
        <input type="{text}" v-model="name">  <!-- Cria um imput que pode ser alterado -->
        <br>

        <a :href="link" target="_blank">Link para o curso!></a> <!-- link se refere à referência do link dentro do script do data devido ao v-bind : -->
    </div>
</template>

<script>
export default {
    data: () => ({          // Função que retorna um objeto
        name: 'Dawidson',    // Retorna um Objeto que tem uma propriedade chamada Dawidson
        link: 'https://treinamento.vuejsbrasil.org',    // Link para o curso
        decoration: 'underline' // decoration definido como underline
    })                      // Tudo que está no data, está interligado com a View
}
</script>
