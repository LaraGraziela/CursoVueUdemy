<template>
  <head>
    <meta charset="UTF-8" />
  </head>

  <h2 class="titulo">Matador de Monstros</h2>

  <div id="all">
    

    <!-- VIDA PLAYER -->
    <div class="painel scores">
      <div class="score">
        <h2>Jogador</h2>
        <div class="life-bar">
          <div
            class="life"
            :class="{ danger: playerLife < 20 }"
            :style="{ width: playerLife + '%' }"
          ></div>
        </div>
        <div>{{ playerLife }}%</div>
      </div>

      <!-- VIDA MONSTRO -->
      <div class="score">
        <h2>Monstro</h2>
        <div class="life-bar">
          <div
            class="life"
            :class="{ danger: monsterLife < 20 }"
            :style="{ width: monsterLife + '%' }"
          ></div>
        </div>
        <div>{{ monsterLife }}%</div>
      </div>
    </div>

    <!-- RESULTADO -->
    <div v-if="hasResult" class="painel result">
      <div v-if="monsterLife == 0" class="win">Você ganhou!!! =)</div>
      <div v-else class="lose">Você perdeu! =(</div>
    </div>

    <!-- BOTÕES -->
    <div class="painel buttons">

        <template v-if="running">

            <button @click="attack(false)" class="btn attack">Ataque</button>

            <button @click="attack(true)" class="btn especial-attack">Ataque Especial</button>

            <button @click="healAndHurt" class="btn heal">Curar</button>

            <button @click="running = false" 
                    class="btn give-up">Desistir</button>
        
        </template>

        <button v-else 
                @click="startGame" 
                class="btn new-game">Iniciar Jogo</button>
    </div>
    <div v-if="logs.length" class="painel logs">
      <ul>
        <li class="log" :key="log" v-for="log in logs" :class="log.cls">{{log.text}}</li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  data: () => ({
    running: false,
    playerLife: 100,
    monsterLife: 100,
    logs: []
    
  }),

  // QUANDO A LUTA ACABAR
  computed: {
    hasResult() {
      return this.playerLife == 0 || this.monsterLife == 0;
    },
  },

  // QUANDO A LUTA FOR INICIADA
  methods: {
      startGame() {
          this.running = true,
          this.playerLife = 100,
          this.monsterLife = 100
          this.logs = []
      },
      
      // VALOR DE ATAQUE
      getRandom(min, max) {
          const value = Math.random() * (max - min) + min
          return Math.round(value)
      },

      //QUANDO ATACAR
      hurt(atr, min, max, especial, source, target, cls){ //source: quem deu dano, target: quem recebeu, cls: classe css.
          const plus = especial ? 5 : 0
          const hurt = this.getRandom(min + plus, max + plus)
          this[atr] = Math.max(this[atr] - hurt, 0) // se der valor negativo pega o 0, se não pega o valor normal.
      
          this.registerLog(`${source} atingiu o ${target} com ${hurt}.` , cls)
      },

      // ATAQUE ESPECIAL
      attack (especial) {
          this.hurt('playerLife',7, 12, false, 'Monstro', 'Jogador', 'monster')// false indica que o player nao pode ser ferido com ataque especial, só o monstro.
          if(this.monsterLife > 0){
              this.hurt('monsterLife',5, 10, especial, 'Jogador', 'Monstro', 'player')
          }
      },

      //CURAR
      heal(min, max){
        const heal = this.getRandom(min, max)
        this.playerLife = Math.min(this.playerLife + heal, 100)
        this.registerLog(`Jogador ganhou força de ${heal}.`, 'player')
      },

      //RECEBER DANO COM A CURA
      healAndHurt() {
        this.heal(10,15)
        this.hurt('playerLife', 7, 12, false, 'Monstro', 'Jogador', 'monster')
      },

      registerLog(text, cls) { //cls = class
        this.logs.unshift({ text, cls })
      }
      
     
  },

  // VOLTAR AO MENU QUANDO HOUVER RESULTADO
  watch: {
      hasResult(value) {
          if (value) this.running = false

      }
  },
};
</script>

<style scoped>

.titulo{
  font-family: "Gill Sans", "Gill Sans MT", Calibri, "Trebuchet MS", sans-serif;
  text-align: center;
}
/* GERAL */
#all {
  font-family: "Gill Sans", "Gill Sans MT", Calibri, "Trebuchet MS", sans-serif;
  display: flex;
  flex-direction: column;
}
.painel {
  margin: 10px;
  padding: 20px;
  box-shadow: 0 2px 10px rgb(0, 0, 0, 0.15);
}

/* AREA DE PONTOS */
.scores {
  display: flex;
}
.score {
  flex: 1;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
.score h2 {
  font-weight: 300;
  font-size: 1.5rem;
}
.life-bar {
  width: 80%;
  height: 20px;
  border: 1px solid #aaa;
}
.life-bar .life {
  display: flex;
  justify-content: center;
  height: 100%;
  background-color: green;
}
.life-bar .life.danger {
  background-color: red;
}

/* ÁREA DO RESULTADO */

.result {
  display: flex;
  justify-content: center;
  font-size: 1.3rem;
  font-weight: 400;
}

.result .win {
  color: green;
}
.result .lose {
  color: red;
}

/* ÁREA DOS BOTÕES */
.buttons {
    display: flex;
    justify-content: center;
    
}
.btn {
    padding: 5px 10px;
    margin: 0px 10px;
    border: 10px;
    text-transform: uppercase;
    font-size: 14px;
    border-radius: 5px;
}
.new-game{
    background-color: rgb(204, 12, 102);
    color: white;
    border-radius: 5px;
}
.attack{
    background-color: rgb(27, 125, 252);
    color: white;
}
.especial-attack{
    background-color: rgb(255, 230, 0);
    color: rgb(91, 97, 7);
}
.heal{
    background-color: rgb(0, 206, 17);
    color: white;
}
.give-up{
    background-color: rgb(41, 61, 55);
    color: white;
}

/* LOGS */
.logs ul{
  display: flex;
  flex-direction: column;
  list-style: none;
  padding: 0;
  margin: 0;
}
.logs ul li {
  display: flex;
  justify-content: center;
  margin: 4px 0px;
  padding: 3px 0px;
  font-weight: 600;
  font-size: 15px;
  text-transform: uppercase;
  border-radius: 5px;

}
.player{
  background-color: cornflowerblue;
  color: white;
}
.monster{
  background-color: crimson;
  color: white;
}
</style>