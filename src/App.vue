<template>
  <div id="app">
    conservé
    <div>
      <Dice
        v-for="(dice, index) in keeped"
        :key="index"
        :value="dice"
        :keeped="true"
      />
    </div>
    <div>
      En jeux
      <Dice
        v-for="(dice, index) in dices"
        @change="keep(index)"
        :value="dice"
        :keeped="false"
        :key="index"
      />
    </div>
    <button @click="roll()">Lancer les dés</button>
    <button @click="reset()">reset</button>
  </div>
</template>

<script>
import Dice from './components/Dice.vue';

export default {
  name: 'app',
  components: {
    Dice,
  },
  data() {
    return {
      dices: [null, null, null],
      keeped: [],
    };
  },
  methods: {
    roll() {
      this.dices = this.dices.map(() => Math.floor(Math.random() * (6 - 1)) + 1);
    },
    keep(index) {
      const result = this.dices.splice(index, 1);
      this.keeped.push(result[0]);
    },
    reset() {
      this.dices = [null, null, null];
      this.keeped = [];
    },
  },
};
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
