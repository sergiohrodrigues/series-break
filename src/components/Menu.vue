<template>
    <section>
        <div>
            <span>Series Break</span>
            <i class="fa-solid fa-dumbbell"></i>
        </div>
        <button @click="ativarModoEscuro">{{ ativarBotao }}</button>
    </section>
</template>

<script lang="ts">
    import { defineComponent } from 'vue';

    export default defineComponent({
        name: 'MenuC',
        data(){
            return{
                modoEscuro: false,
                ativarBotao: 'Ativar modo escuro'
            }
        },
        emits:['temaAlterado'],
        methods:{
            ativarModoEscuro(){
                this.modoEscuro = !this.modoEscuro
                this.$emit('temaAlterado', this.modoEscuro)
                if(this.modoEscuro){
                    this.ativarBotao = 'Desativar modo escuro'
                }else {
                    this.ativarBotao = 'Ativar modo escuro'
                }
            }
        }
    })
</script>

<style scoped>
    section{
        display: flex;
        flex-direction: column;
        align-items: center;
        gap: 1rem;
        padding: 0.5rem 0;
    }
    span{
        font-size: 1.5rem;
        margin-right: 0.5rem;
    }
    i{
        font-size: 1.5rem;
    }
    
    @media screen and (min-width: 768px){
        section{
            justify-content: flex-start;
            padding: 2rem 1rem;
            margin-left: 0;
            min-width: 284px;
        }

        span{
            font-size: 2.5rem;
        }

        i{
            font-size: 2rem;
        }

        button{
            padding: 0.5rem;
        }
    }

</style>