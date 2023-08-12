<template>
  <main>
    <Menu />
    <section>
      <div style="text-align: center;">
        <h2 style="margin-bottom: 0.5rem;">Qual o intervalo de descanso?</h2>
        <!-- <div style="display: flex; justify-content: center; gap: 1rem; margin: 1rem 0;">
          <button>30</button>
          <button>60</button>
          <button>90</button>
          <button>120</button>
        </div> -->
        <!-- <h2 style="text-align: center;">Digite outro valor:</h2> -->
        <input :disabled="intervalo !== 0" v-model="inputDescanso" type="number" placeholder="numero em segundos">
      </div>
      <div style="text-align: center;">
        <h2 style="margin-bottom: 0.5rem;">Qual o numero de séries?</h2>
        <!-- <div style="display: flex; justify-content: center; gap: 1rem; margin: 1rem 0;">
          <button>2</button>
          <button>3</button>
          <button>4</button>
        </div> -->
        <!-- <h2 style="text-align: center;">Digite outro valor:</h2> -->
        <input :disabled="series !== 0" v-model="inputSeries" type="number" placeholder="quantas séries?">
      </div>
      <button :disabled="series !== 0" style="margin-top: 0.5rem; padding: 0.5rem;" @click="adicionarTemporizador">Adicionar</button>
    </section>
    <Botao :input="intervalo" :series="series"/>
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
      series: 0
    }
  },
  methods:{
    adicionarTemporizador(){
      if(this.inputDescanso == '' ||this.inputSeries == ''){
        alert("Por favor preencha os dois campos")
      } else{
        this.intervalo = parseInt(this.inputDescanso)
        this.series = parseInt(this.inputSeries)
        this.inputDescanso = ''
        this.inputSeries = ''
      }
    }
  }
});
</script>

<style scoped>
  @import url(./assets/reset.css);

  section{
    margin-top: 2rem;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    gap: 0.5rem;
  }
  input{
    text-align: center;
  }
</style>