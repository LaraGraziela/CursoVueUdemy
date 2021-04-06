<template>
    <div id="all">
        <h2>{{titulo}}</h2>
        
        <button class="btn" @click="alteratitulo">Alterar título</button> |
        <button class="btn" @click="$destroy()">Destruir</button>
    <br><br>
        <p>PRE</p>
        
        <pre>
            Texto embaixo de acordo com a digitação:

            Lara Graziela Diogo
            Rua Antônio Severino de Castro
            13
            Floramar
            Belo Horizonte
            Minas Gerais
        </pre>

        <p>STRONG, EM, SMALL</p>
        <strong>Negrito: Lara</strong><br>
        <em>Itálico: Graziela</em><br>
        <small>Texto pequeno: Diogos</small><br><br><br><hr><br>

        <h2>Contadores</h2>
        <div class="contador">
            

            <span>{{contador}}</span>
            <button @click="adicionar"> + </button>
            <button @click="subtrair"> - </button>
        </div>
    </div>
  
</template>

<script>
export default {
    data: () => ({
        titulo: 'Ciclo de vida VUE!',
        contador: 0,
    }),

    beforeCreate(){
        console.log('Antes de criar.')
    },
    created(){
        console.log('Criado.')
    },
    beforeMount(){
        console.log('Antes de montar (DOM)')
    },
    mounted() {
        console.log('DOM montada.')
    },
    beforeUpdate(){
        console.log('Antes de atualizar.')
    },
    updated(){
        console.log('Atualizado.')
    },
    beforeUnmountDestroy(){
        console.log('Antes de destruir.')
    },
    destroy(){
        console.log('Destruído')
    },

    methods: {
        alteratitulo() {
            this.titulo += ' #'
        },
        adicionar() {
            this.contador++
        },
        subtrair() {
            this.contador--
        }
    }
    
}
</script>

<style scoped>
#all{
    text-align: center;
  font-family: "Gill Sans", "Gill Sans MT", Calibri, "Trebuchet MS", sans-serif;
}
.btn{
    background-color: rgb(51, 201, 108);
    color: white;
    
}
.contador span{
    border-bottom: 1px solid rgb(17, 189, 2);
    height: 30px;
    padding: 5px 25px;
}
.contador button {
    height: 30px;
    width: 30px;
    border-radius: 15px;
    background-color:coral;
    margin-left: 10px;
    outline: none;

}
</style>

