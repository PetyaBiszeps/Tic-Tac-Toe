<script lang="ts" setup>
import { GameView } from '@/components/GameView/GameViewData.ts';
import { players } from './Constants.ts';
</script>

<template>
  <h1>{{GameView.handleMessage()}}</h1>

  <div class="gameField">
    <div class="wrapper">
      <div v-for="(value, key) in GameView.boardState.value" :key="key" class="cell" @click="GameView.handleClick(key)">
        {{value === players.p1.value ? 'X' : value === players.p2.value ? 'O' : '' }}
      </div>
    </div>
  </div>
</template>

<style scoped>
h1 {
  text-align: center;
}

.gameField {
  border-radius: 0.75rem;
  background: var(--bg-welcome);
  border: 2px solid var(--border);
  padding: clamp(0rem, 1.25vw, 1.25rem);
}

.wrapper {
  display: grid;
  border-radius: 1rem;
  grid-gap: clamp(0.5rem, 1vw, 2rem);
  grid-template-columns: repeat(3, 1fr);
  padding: clamp(0.25rem, 1.25vw, 1.25rem);
}

.cell {
  width: 6rem;
  height: 6rem;

  display: inline-flex;
  align-items: center;
  justify-content: center;

  cursor: pointer;
  font-size: 6rem;
  border-radius: 1rem;
  border: 2px solid var(--border);
}

.cell:hover {
  animation: cellAnimation 0.15s linear 1 normal forwards;
}

@keyframes cellAnimation {
  from {
    background: white;
  }

  to {
    background: var(--bg-hover);
  }
}
</style>
