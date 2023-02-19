<script setup lang="ts">
defineProps<{
  life: number;
  playing: boolean;
}>();

defineEmits(['sub', 'add', 'modify']);
</script>

<template>
  <div class="box">
    <div class="setter" @click="$emit('sub')" v-bind:class="{ 'red': playing }"> - </div>
    <div class="life green" @click="$emit('modify')"  v-bind:class="{ 'red': playing }">{{ life }}</div>
    <div class="setter" @click="$emit('add')"> + </div>
  </div>
</template>

<style scoped>
h1 {
  font-weight: 500;
  font-size: 2.6rem;
  top: -10px;
}

.life {
  font-size: 3rem;
  min-width: 51.750px;
  text-align: center;
}

.setter {
  font-size: 1.5rem;
  margin: 0.5rem;
  cursor: pointer;
  -webkit-touch-callout: none;
  -webkit-user-select: none;
  -khtml-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}

.box {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
}

.setter.red {
  cursor: not-allowed;
}

/* @media (min-width: 1024px) {
} */
</style>
