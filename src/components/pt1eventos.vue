<template>
    <div id="all">
        <h2>Eventos</h2>

        <button class="btn" @click="somar">Somar</button> |
        <button class="btn" @click="subtrair">Subtrair</button>
        <p>{{contador}}</p>
        <p>{{contador >= 0 ? 'Número positivo.' : 'Numero Negativo.'}}</p><br>

        <p @mousemove="attXY">Mouse: {{x}} e {{y}}
            <span class="mousestop" @mousemove.stop="">   PARAR O MOUSE </span>
        </p><br>

        <p>Digite e dê enter para ver o alerta:</p>
        <input type="text" @keyup.enter="alerta">

    </div>
  <hr>

</template>

<script>
export default {
    data: () => ({
        contador: 0,
        x: 0,
        y: 0

    }),

    watch: {
        contador() {
            if (this.contador === 10){
                console.log('Passou de 10.')
            }else{
                console.log('Ainda não é 10.')
            }
        }
        
    },

    methods: {
        somar() {
            this.contador = this.contador + 1
            //OU
            //this.contador++
        },
        subtrair () {
            this.contador = this.contador - 1
            //OU
            //this.contador--
        },
        attXY (evento) {
            this.x = evento.clientX
            this.y = evento.clientY
            console.log(evento)
        },
        alerta () {
            alert('Alerta!')
        }
    }

}
</script>

<style scoped>
#all{
    align-items: center;
  text-align: center;
  font-family: "Gill Sans", "Gill Sans MT", Calibri, "Trebuchet MS", sans-serif;
}
.mousestop{
    background-color: pink;
}

.btn{
    background-color: rgb(51, 201, 108);
    color: white;
}

</style>