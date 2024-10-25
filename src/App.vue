<script setup>
import { ref } from 'vue'
const players = ref([
  {
    id: 1,
    alias: 'Alfred',
    gender: 'male',
    age: 32,
    level: 'Expert',
    numberOfWin: 2,
    actualScore: 0,
  },
  {
    id: 2,
    alias: 'Lisa',
    gender: 'female',
    age: 29,
    level: 'Intermediate',
    numberOfWin: 1,
    actualScore: 0,
  },
])
console.log(players.value[1])
</script>

<template>
  <main>
    <h1>ScoreBoard</h1>
    <br />
    <section>
      <div v-for="infos in players" :key="infos.id">
        <h3>{{ infos.alias }}</h3>
        <p>{{ infos.age }} ans</p>
        <p>level {{ infos.level }}</p>
        <h4>
          {{ infos.gender === 'female' ? 'She' : 'He' }} has already
          <span>{{ infos.numberOfWin }}</span>
          {{ infos.numberOfWin > 1 ? 'victories' : 'victory' }}
        </h4>
        <h2>Actual score</h2>

        <div class="actualScore">
          <p>
            {{ infos.actualScore }}
          </p>
        </div>

        <div class="buttonScore">
          <button @click="infos.actualScore = infos.actualScore + 1">
            add 1 point
          </button>
          <button @click="infos.actualScore = infos.actualScore + 2">
            add 2 points
          </button>
          <button @click="infos.actualScore = infos.actualScore + 5">
            add 5 points
          </button>
        </div>
      </div>
      <div class="lineCenter"></div>
    </section>
    <div class="reset">
      <button
        @click="(players[0].actualScore = 0), (players[1].actualScore = 0)"
      >
        Reset
      </button>
    </div>
  </main>
</template>

<style scoped>
span {
  color: #fb7041;
}
h1 {
  text-align: center;
  margin-top: 20px;
  margin-bottom: 50px;
  font-size: 40px;
  font-weight: bold;
  color: #fb7041;
}
h2 {
  font-weight: bold;
  font-size: 30px;
}
h3 {
  font-weight: bold;
  font-size: 20px;
}
h4 {
  font-weight: bold;
  margin-bottom: 20px;
  margin-top: 20px;
}
p {
  font-size: 12px;
}

section {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 70px;
}
section > div {
  /* border: 1px solid red; */
  text-align: center;
  display: flex;
  flex-direction: column;
  align-items: center;
}
.buttonScore {
  /* border: 1px solid blue; */
  display: flex;
  gap: 20px;

  margin-top: 20px;
}
.buttonScore button {
  border-radius: 5px;
  border-color: #fb7041;
  color: #fb7041;
  background-color: transparent;
  padding: 5px;
}
.reset {
  /* border: 1px solid red; */
  text-align: center;
  margin-top: 50px;
}
button {
  border: 1px solid;
}
button:hover {
  background-color: #fb7041;
  color: white;
  transform: scale(1.2);
}
.reset button {
  border-radius: 5px;
  background-color: rgba(211, 211, 211, 0.327);
  padding: 5px 10px;
  color: gray;
  border: 1px solid gray;
}
.reset button:hover {
  background-color: gray;
  color: white;
  transform: scale(1.2);
}
.actualScore {
  /* border: 1px solid purple; */
  border-radius: 100%;
  width: 50px;
  height: 50px;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #fb7141;
  margin-top: 10px;
}
.actualScore p {
  font-size: 32px;
}
.lineCenter {
  width: 3px;
  height: 240px;
  background-color: lightgray;
  position: absolute;
}
</style>
