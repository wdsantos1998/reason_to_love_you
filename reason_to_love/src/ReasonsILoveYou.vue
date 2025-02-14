<template>
  <div class="valentine-background">
    <h1 class="main-title">Reasons I Love You, Rachel ❤️</h1>
    <img src="/couple_picture.jpeg" alt="Couple Picture" class="couple-img" />
    <div class="love-note">
      <div v-show="!startGameState && !finishGameState" class="welcome">
        <h2 class="title">For Whenever You Need a Reminder...</h2>
        <p class="subtitle">Click "Get a Reason" to feel the love. 💌</p>
      </div>
      <div v-show="isGameOver" class="game-over">
        <h2 class="title">You Have the Best Boyfriend Ever! 🥰</h2>
      </div>
      <div v-show="startGameState && !finishGameState && !isGameOver" class="display-reason">
        <span class="reason-text">{{ displayReason }}</span>
        <button class="heart-button" @click="getNextReason">💖 Next Reason</button>
      </div>
      <div v-show="!startGameState && finishGameState" class="thank-you">
        <h2 class="title">Thank you for stopping by! 💕</h2>
        <button class="heart-button" @click="startGame">Fall In Love Again</button>
      </div>
    </div>
    <button class="heart-button" @click="startGame" v-if="!startGameState && !finishGameState && !isGameOver">💌 Get a
      Reason
    </button>
    <button class="stop-button" @click="finishGame" v-if="startGameState && !finishGameState && !isGameOver">💔 Stop
    </button>
  </div>
</template>

<script>
export default {
  name: "ReasonsILoveYou",
  data() {
    return {
      reasons: [
        {index: 1, reason: "She always knows how to make me smile, no matter the situation."},
        {index: 2, reason: "Her laugh is the most beautiful sound in the world to me."},
        {index: 3, reason: "She supports me in my goals and encourages me to be my best self."},
        {index: 4, reason: "Her kindness and compassion for others inspire me every day."},
        {index: 5, reason: "She listens to me attentively and genuinely cares about what I have to say."},
        {index: 6, reason: "Her hugs feel like home, comforting and safe."},
      ],
      startGameState: false,
      finishGameState: false,
      isGameOver: false,
      currentReason: "",
    };
  },
  methods: {
    startGame() {
      this.getNextReason();
      this.startGameState = true;
      this.finishGameState = false;
    },
    getNextReason() {
      const randomIndex = Math.floor(Math.random() * this.reasons.length);
      this.currentReason = this.reasons[randomIndex].reason;
    },
    finishGame() {
      this.finishGameState = true;
      this.startGameState = false;
    },
  },
  computed: {
    displayReason() {
      return this.currentReason || "Click 'Get a Reason' to start!";
    },
  },
};
</script>

<style scoped>
.valentine-background {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
  background: linear-gradient(to bottom right, #ff758c, #ff7eb3);
  font-family: "Cursive", Arial, sans-serif;
  text-align: center;
}

.main-title {
  font-size: 3rem;
  font-weight: bold;
  color: white;
  margin-bottom: 10px;
}

.couple-img {
  width: 250px;
  height: 250px;
  border-radius: 50%;
  box-shadow: 0 0 10px rgba(255, 255, 255, 0.5);
  margin-bottom: 20px;
}

.love-note {
  background-color: white;
  padding: 20px;
  border-radius: 20px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
  width: 80%;
  max-width: 400px;
}

.title {
  font-size: 2rem;
  color: #ff4f81;
}

.subtitle {
  font-size: 1.2rem;
  color: #333;
}

.reason-text {
  font-size: 1.5rem;
  color: #d6336c;
  font-weight: bold;
  margin: 20px 0;
}

.heart-button {
  background-color: #ff4f81;
  color: white;
  font-size: 18px;
  border: none;
  border-radius: 50px;
  padding: 12px 24px;
  cursor: pointer;
  transition: 0.3s;
}

.heart-button:hover {
  background-color: #ff6f91;
}

.stop-button {
  background-color: #ff4f4f;
  color: white;
  font-size: 18px;
  border: none;
  border-radius: 50px;
  padding: 12px 24px;
  margin-top: 10px;
  cursor: pointer;
  transition: 0.3s;
}

.stop-button:hover {
  background-color: #ff7070;
}
.display-reason{
  display: flex;
  flex-direction: column;
  align-items: center;
  row-gap: 20px;
}
</style>
