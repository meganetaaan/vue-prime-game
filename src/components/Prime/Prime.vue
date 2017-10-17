<template>
  <div class="prime-game">
    <template v-if="ready">
      <div>score: {{score}}</div>
      <div v-if="number">is {{number}} prime?</div>
      <input type="button" value="prime" @click="prime">
      <input type="button" value="notPrime" @click="notPrime">
    </template>
    <template v-else>
      <div>high score: {{highScore}}</div>
      <input type="button" value="start" @click="start">
    </template>
  </div>
</template>

<script>
import math from 'mathjs'
export default {
  name: 'Prime',
  data () {
    return {
      number: null,
      ready: false,
      score: 0,
      highScore: 0,
      time: 0,
      correct: null
    }
  },
  methods: {
    start () {
      this.time = 0
      this.ready = true
      this.next()
    },
    next () {
      this.number = math.round(math.random(0, 100))
      this.time += 1
      if (this.time >= 10) {
        this.finish()
      }
    },
    finish () {
      this.highScore = this.score
      this.ready = false
    },
    prime () {
      this.judge(math.isPrime(this.number), this.number)
    },
    notPrime () {
      this.judge(!math.isPrime(this.number), math.max(2, math.floor(this.number / 10)))
    },
    judge (condition, bet) {
      if (condition) {
        this.score += bet
      } else {
        this.score = math.max(this.score - bet, 0)
      }
      this.next()
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
