<template>

    <div id="all">
        <h2>Desafio 2</h2>

        <button class="btn" @click="alerta">Clique</button><br /><br /><br />

        <p>Evento Keydown:</p>
        <input type="text" @keydown.enter="alteraValor" />
        <p>{{ valor }}</p>
        <br />
        <hr>
        
        <!-- DESAFIO 3 -->
        <h2>Desafio 3</h2>
        <p>Valor atual: {{ valor2 }}</p>
        <button class="btn" @click="valor2 += 5">Somar 5</button> |
        <button class="btn" @click="valor2 += 1">Somar 1</button> |
        <button class="btn" @click="valor2 -= 5">Subtrair 5</button>
        <p>Resultado: {{ resultado }}</p>
        <hr>
    </div>
</template>

<script>
export default {
    data: () => ({
        valor: '',
        valor2: 0
    }),

    methods: {
        //DESAFIO 2
        alerta () {
            alert ('Alerta')
        },
        alteraValor (event) {
            this.valor = event.target.value
        }
    },

    //DESAFIO 3
    computed: {

        resultado() {
            //return this.valor2 == 37 ? 'Valor igual a 37.' : 'Valor diferente.'
            if(this.valor2 == 37) {
                return 'Valor igual a 37'
            }else{
                  return 'Valor Diferente.'
                 }
            
        }
    },

    watch: {
        resultado() {
            setTimeout(() => {
                this.valor2 = 0
            }, 5000)
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

</style>
