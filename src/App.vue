<script setup>
  import {reactive} from 'vue';
  import PreJogo from './components/preJogo.vue';
  import Game from './components/game.vue';
  const state = reactive({tela: 'inicio'});
</script>

<template>
  <main id="app">
    <section v-if="state.tela === 'inicio'" id="inicio">
      <PreJogo :state="state" />
    </section>
    <section v-if="state.tela === 'game'" id="game">
      <Game :gameData="state.gameData" />
    </section>
  </main>
</template>

<style scoped>
  #app{
    width: 100%;
    height: 100vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
}
  #inicio{
    width: 30rem;
  }
</style>
