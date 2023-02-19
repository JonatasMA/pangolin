<script setup lang="ts">
import LifeCounter from "./counters/LifeCounter.vue";
import DotCounter from "./counters/DotCounter.vue";

defineProps<{
  name: string;
  life: number;
  poison: number;
  commanderZone: number;
}>();

function promptName(text) {
  var value = prompt(text);
  if (value == '') {
    return 'Player';
  }
  return value;
}

function promptLife(text, life) {
  var value = parseInt(prompt(text));
  if (value) {
    return value;
  }
  return life;
}

</script>

<template>
  <div class="container">
    <h3 class="green" @click="name = promptName('Nome')" v-bind:class="{ 'red': life == 0 || poison >= 10 }">{{ name }}</h3>
    <LifeCounter v-bind:playing="life == 0 || poison >= 10" v-bind:life=life @add="() => { life++; }" @sub="() => { life > 0 ? life-- : life = 0; }" @modify="() => { life = promptLife('Nova vida', life); }" />
    <div class="box">
      <DotCounter v-bind:value=poison @click="() => { poison++; }" type="poison" />
      <DotCounter v-bind:value=commanderZone  @click="() => { commanderZone++; }" type="commanderZone" />
    </div>
  </div>
</template>

<style scoped>
h3 {
  font-size: 1.2rem;
}

.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  background-color: black;
  border: 0.1rem solid white;
}

.box {
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>
