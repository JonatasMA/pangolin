<script setup lang="ts">
defineProps<{
  value: number;
  type: string;
}>();
defineEmits(['click']);
</script>

<template>
  <div class="dot" v-bind:class="{ 'green': type == 'poison' }" @click="$emit('click')">
    {{ value }}
  </div>
</template>

<style scoped>
.dot {
  background-color: white;
  color: black;
  border-radius: 50%;
  min-width: 30px;
  min-height: 30px;
  text-align: center;
  margin: 2.5px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: 600;
  cursor: pointer;
  -webkit-touch-callout: none;
  -webkit-user-select: none;
  -khtml-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}

.green {
  color: green;
}
</style>
