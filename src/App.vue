<template>
  <main :class="{'modo-escuro': modoEscuroAtivo}">
    <Menu @temaAlterado="trocarTema"/>
    <section>
      <div style="text-align: center;">
        <h2 style="margin-bottom: 0.5rem;">Qual o intervalo de descanso em segundos?</h2>
        <!-- <div style="display: flex; justify-content: center; gap: 1rem; margin: 1rem 0;">
          <button>30</button>
          <button>60</button>
          <button>90</button>
          <button>120</button>
        </div> -->
        <!-- <h2 style="text-align: center;">Digite outro valor:</h2> -->
        <input :disabled="intervalo !== 0" v-model="inputDescanso" type="number" placeholder="Ex: 30, 60, 90">
      </div>
      <div style="text-align: center;">
        <h2 style="margin-bottom: 0.5rem;">Qual o numero de séries?</h2>
        <!-- <div style="display: flex; justify-content: center; gap: 1rem; margin: 1rem 0;">
          <button>2</button>
          <button>3</button>
          <button>4</button>
        </div> -->
        <!-- <h2 style="text-align: center;">Digite outro valor:</h2> -->
        <input :disabled="series !== 0" v-model="inputSeries" type="number" placeholder="Ex: 3, 4, 5">
      </div>
      <button :disabled="series !== 0" style="margin-top: 0.5rem; padding: 0.5rem;" @click="adicionarTemporizador">Adicionar</button>
      <Botao :input="intervalo" :series="series"/>
    </section>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import Menu from './components/Menu.vue';
import Botao from './components/Botao.vue';

export default defineComponent({
  name: 'App',
  components: { Menu, Botao },
  data(){
    return {
      inputDescanso: '',
      intervalo: 0,
      inputSeries: '',
      series: 0,
      modoEscuroAtivo: false
    }
  },
  methods:{
    adicionarTemporizador(){
      if(this.inputDescanso == '' || this.inputSeries == ''){
        alert("Por favor preencha os dois campos")
      } else if(parseInt(this.inputDescanso) < 0 || parseInt(this.inputSeries) < 0){
        alert("Por favor insira valores maiores do que 0.")
        this.inputDescanso = ''
        this.inputSeries = ''
      }else {
        this.intervalo = parseInt(this.inputDescanso)
        this.series = parseInt(this.inputSeries)
        this.inputDescanso = ''
        this.inputSeries = ''
      }
    },
    trocarTema(modoEscuroAtivo: boolean){
      this.modoEscuroAtivo = modoEscuroAtivo
    }
  }
});
</script>

<style>
  @import url(./assets/reset.css);

  body{
    --background: #343633;
    --fonte: #fff;
    min-height: 100vh;
    min-width: 260px;
  }

  section{
    padding-top: 3rem;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    gap: 0.5rem;
  }
  
  input{
    text-align: center;
  }

  h2{
    font-size: 1.3rem;
  }

  .modo-escuro{
    background-color: var(--background);
    color: var(--fonte);
    min-height: 100vh;
  }

  input{
    padding: 0.5rem;
    outline: none;
  }

  @media screen and (min-width: 768px){
    main{
      display: flex;
    }
    section{
      padding-top: 2rem;
      margin-left: 10%;
      justify-content: flex-start;
    }
  }
</style>