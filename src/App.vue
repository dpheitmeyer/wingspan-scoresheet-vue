<script setup>
import { ref, computed } from 'vue'

const players = ref([
  {
    name: 'Player 1',
    birds: 0,
    bonus: 0,
    round: 0,
    eggs: 0,
    cached: 0,
    tucked: 0,
  },
  {
    name: 'Player 2',
    birds: 0,
    bonus: 0,
    round: 0,
    eggs: 0,
    cached: 0,
    tucked: 0,
  },
  {
    name: 'Player 3',
    birds: 0,
    bonus: 0,
    round: 0,
    eggs: 0,
    cached: 0,
    tucked: 0,
  },
  {
    name: 'Player 4',
    birds: 0,
    bonus: 0,
    round: 0,
    eggs: 0,
    cached: 0,
    tucked: 0,
  },
  {
    name: 'Player 5',
    birds: 0,
    bonus: 0,
    round: 0,
    eggs: 0,
    cached: 0,
    tucked: 0,
  },
])

const getPlayerTotal = (player) => {
  return player.birds + player.bonus + player.round + player.eggs + player.cached + player.tucked
}
const getHighestScore = computed(() => {
  /* calculate all player scores and get the highest */
  let totalForPlayers = players.value.map((player) => {
    return getPlayerTotal(player)
  })
  /* FIX FROM CLASS: Math.max uses a list of numbers as in
  Math.max(1,2,3), not an array.  So, I need to "spread" the Array
  into its individual items with ...
  Math.max(...totalForPlayers)
  */
  let highScore = Math.max(...totalForPlayers)

  console.log(totalForPlayers)
  console.log(`high score ${highScore}`)
  return highScore
})

const isWinner = (player) => {
  let playerTotal = getPlayerTotal(player)
  /* FIX FROM CLASS: Since getHighestScore is a Vue "computed" value,
  I need to refer to getHighestScore.value to get the value instead of the
  computed object that Vue created to wrap the value so that it can do
  its Vue 'magic'
  */
  if (playerTotal > 0 && playerTotal === getHighestScore.value) {
    return true
  } else {
    return false
  }
}
</script>

<template>
  <div id="app">
    <h1>Wingspan Scoresheet</h1>
    <div class="scoresheet">
      <div
        v-for="(player, index) in players"
        :key="index"
        class="player"
        :class="{ winner: isWinner(player) }"
      >
        <h2>{{ player.name }}</h2>
        <div class="points">
          <label>Birds</label> <input class="points" v-model.number="player.birds" />
        </div>
        <div class="points">
          <label>Bonus Cards</label> <input class="points" v-model.number="player.bonus" />
        </div>
        <div class="points">
          <label>Round End Goals</label> <input class="points" v-model.number="player.round" />
        </div>
        <div class="points">
          <label>Eggs</label> <input class="points" v-model.number="player.eggs" />
        </div>
        <div class="points">
          <label>Cached Food</label> <input class="points" v-model.number="player.cached" />
        </div>
        <div class="points">
          <label>Tucked Cards</label> <input class="points" v-model.number="player.tucked" />
        </div>
        <div class="total">Total: {{ getPlayerTotal(player) }}</div>
      </div>
    </div>
  </div>
</template>

<style global>
body {
  font-family: arial, helvetica, sans-serif;
}
</style>
<style scoped>
.player {
  border: thin solid black;
  padding: 0.25rem;
}
.scoresheet {
  display: grid;
  column-gap: 0.5rem;
  grid-template-columns: repeat(5, 1fr);
}
.points {
  margin-bottom: 0.5rem;
}
.total {
  font-weight: bold;
  font-size: 2rem;
  margin-top: 1rem;
}
.winner {
  background-color: lime;
}
label {
  display: block;
  margin-bottom: 0.1rem;
}
input {
  display: block;
  font-size: 1.5rem;
  width: 5rem;
  text-align: right;
}
</style>
