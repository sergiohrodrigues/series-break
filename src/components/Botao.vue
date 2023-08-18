<template>
    <section>
        <span v-if="mudarExercicio">Voce está na {{ numeroDeSeries }}° série.</span>
        <span v-else style="text-align: center;">Exercicio finalizado,<br> clique em Mudar Exercicio.</span>
        <button class="descansar" v-if="tempoRodando" @click="iniciar" :disabled="tempoRodando || input == 0 || mudarExercicio === false" >{{ tempoEmSegundos }}</button>
        <button class="descansar" v-else @click="iniciar" :disabled="tempoRodando || input == 0 || mudarExercicio === false">Intervalo</button>
        <button class="novo-exercicio" :disabled="mudarExercicio" @click="functionMudarExercicio">Mudar Exercicio</button>
    </section>
</template>

<script lang="ts">
    import { defineComponent } from 'vue';

    export default defineComponent({
        name: "BotaoC",
        data(){
            return{
                cronometro: 0,
                tempoEmSegundos: this.input,
                tempoRodando: false,
                numeroDeSeries: 1,
                mudarExercicio: true
            }
        },
        props:{
            input: {
                type: Number
            },
            series:{
                type: Number
            }
        },
        methods: {
            iniciar(){
                this.tempoEmSegundos = this.input
                this.cronometro = setInterval(() => {
                    this.tempoEmSegundos! -= 1
                    this.tempoRodando = true
                        if(this.tempoEmSegundos === -1){
                            clearInterval(this.cronometro)
                            this.tempoRodando = false
                            this.tempoEmSegundos = this.input
                            this.numeroDeSeries += 1
                            if(this.numeroDeSeries > this.series!){
                                this.numeroDeSeries = 1
                                this.mudarExercicio = false
                            }
                        }
                    }, 1000)
            },
            functionMudarExercicio(){
                this.mudarExercicio = true
            }
        }
    })
</script>

<style scoped>
    section{
        padding-top: 2rem;
    }
    .descansar{
        background-color: green;
        border-radius: 50%;
        width: 150px;
        height: 150px;
        border: none;
        font-size: 1.5rem;
        margin-top: 1rem;
    }
    .novo-exercicio{
        margin: 1rem 0 3rem 0;
        padding: 0.5rem;
    }

    span{
        font-size: 1.3rem;
    }

    @media screen and (min-width: 768px){
        section{
            margin-left: 0;
        }

        span{
            font-size: 2rem;
        }
    }
</style>