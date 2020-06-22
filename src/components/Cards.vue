<template>
  <div class="mt-48">
    <div class="flex justify-center">
      <img src="../assets/hand.jpg" alt="hand" />
      <div class="flex justify-center">
        <div
          v-bind:class="{ 
          'bg-blue-700': card === 'blue',
          'bg-red-700': card === 'red',
       }"
          class="w-16 h-32 mr-4"
          :key="card"
          v-for="card in hand"
        >{{card}}</div>
      </div>
    </div>

    <div @click="drawCard" class="flex flex-col items-center mt-12">
      <div
        class="w-16 h-32 border border-black flatCard"
        v-bind:class="{ 
          'bg-blue-700': card === 'blue',
          'bg-red-700': card === 'red',
       }"
        :key="card"
        v-for="card in deck"
      >{{ card }}</div>
    </div>
  </div>
</template>

<style scoped>
.flatCard {
  transform: rotate3d(9, -8, 11, 101deg);
  margin: -60px;
}
</style>

<script>
function shuffle(array) {
  return [...array].sort(() => Math.random() - 0.5);
}

function _drawCard(deck) {
  const drawnCard = [...deck][0];
  return {
    drawnCard,
    newDeck: deck.slice(1)
  };
}

let deck = [];
let hand = [];

for (let count = 0; count < 17; count++) {
  if (count < 6) {
    deck.push("blue");
  } else {
    deck.push("red");
  }
}

// the policy deck is shuffled
deck = shuffle(deck);
console.log("hand", hand);

export default {
  name: "Cards",
  methods: {
    drawCard() {
      console.log("clicking");
      if (this.hand.length === 3) {
        return;
      }
      const top = this.deck.shift();
      this.hand.push(top);
    }
  },
  data() {
    return {
      deck,
      hand
    };
  }
};
</script>
