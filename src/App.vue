<script setup lang="ts">
import PlayerContainer from "./components/PlayerContainer.vue";

let urlParams = new URLSearchParams(window.location.search);
var playersNumber :number = parseInt(urlParams.get('players'));
playersNumber = playersNumber <= 8 ? playersNumber : 4;
var halfPlayers :number = Math.ceil(playersNumber / 2);

var players: Array<object> = new Array(playersNumber);
players.fill({ name: 'Player 1', life: 40, poison: 0, commanderZone: 0 }, 0, playersNumber);

</script>

<template>
  <div class="wrapper" v-bind:class="{ 'grid-4': halfPlayers == 4, 'grid-3': halfPlayers == 3, 'grid-2': halfPlayers == 2 }">
    <PlayerContainer  v-for="(player, index) in players" index="{{ index }}"
      v-bind:class="{ 'rotate-180': halfPlayers > index && playersNumber > 1 }"
      v-model:name="player.name"
      v-model:life=player.life
      v-model:poison=player.poison
      v-model:commanderZone=player.commanderZone
    />
  </div>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

.wrapper {
  display: grid;
  grid-auto-rows: 160px;
}

.grid-4 {
  grid-template-columns: repeat(4, 1fr);
}

.grid-3 {
  grid-template-columns: repeat(3, 1fr);
}

.grid-2 {
  grid-template-columns: repeat(2, 1fr);
}

.rotate-180 {
  transform: rotate(180deg);
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
