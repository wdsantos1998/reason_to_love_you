<template>
  <div class="valentine-background">
    <h1 class="main-title">Reasons I Love You, Rachel ❤️</h1>
    <img src="/couple_picture.jpeg" alt="Couple Picture" class="couple-img" />
    <div class="love-note">
      <div v-show="!startGameState && !finishGameState" class="welcome">
        <h2 class="title">For Whenever You Need a Reminder...</h2>
        <h2 class="title">💌This list is still getting updated as I find more reasons to love you.💌</h2>
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
        {index: 1, reason: "You are the most beautiful person I have ever met, inside and out."},
        {index: 2, reason: "You makes me laugh. Specially when you make the 'GRINGA speaking spanish impersonation'."},
        {index: 3, reason: "You are so beautiful, even when you don't try."},
        {index: 4, reason: "You are so kind and sensitive to others. I love how you care about everyone around you. I still remember that they you stop that man in the institute hall to ask him if he was ok."},
        {index: 5, reason: "You are so smart and talented. The first time I saw you play the piano, I was blown away."},
        {index: 6, reason: "You are an amazing daughter and sister. The way you demonstrate your love for your family is so beautiful. It make me desire to be part of your family."},
        {index: 7, reason: "You are an amazing friend. Not just for me, but for everyone."},
        {index: 8, reason: "You were a faithful sister missionary. This makes me so proud of you. I still remember that day you showed me your scriptures and the notes you took in the mission. A sweet memory."},
        {index: 9, reason: "You learn Portuguese just because of me. This is so sweet. I can see how much you love me in this gesture."},
        {index: 10, reason: "You have a beautiful voice. I love to hear you sing. That Sunday when we were together with your mom at the Church, I was trying to keep up with your beautiful voice."},
        {index: 11, reason: "You makes miracles in the kitchen. I love your food and I love when you cook for me. KEEP DOING IT."},
        {index: 12, reason: "Your touch makes me feel so loved. Specially when you hold my hand."},
        {index: 13, reason: "It's easy to love you and everyone likes you. It's like if you had an magnet to attract good people."},
        {index: 13, reason: "Your smile is so cute! I feel like I'm in heaven when I see you smiling."},
        {index: 14, reason: "Your eyes are so beautiful. I can feel your love when you look at me."},
        {index: 15, reason: "I love that you want to serve your country. You make me proud."},
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
  padding: 10px 20px;
  flex-direction: column;
  align-items: center;
  height: 100vh;
  justify-content: center;
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
  font-size: 1.2rem;
  color: #ff4f81;
}

.subtitle {
  font-size: 1rem;
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
  margin-top: 20px;
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
  margin-top: 20px;
  cursor: pointer;
  transition: 0.3s;
}

.stop-button:hover {
  background-color: #ff7070;
}
.display-reason{
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  width: 100%;
  align-items: center;
  row-gap: 20px;
  height: 300px;
}
.welcome {
  display: flex;
  flex-direction: column;
  align-items: center;
  row-gap: 20px;
}
@media only screen and (max-width: 600px) {
  .valentine-background {
    display: flex;
    padding: 0 20px;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 90%;
    background: linear-gradient(to bottom right, #ff758c, #ff7eb3);
    font-family: "Cursive", Arial, sans-serif;
    text-align: center;
  }
  .display-reason{
    display: flex;
    flex-direction: column;
    align-content: center;
    width: 100%;
    align-items: center;
    row-gap: 10px;
  }
  .reason-text {
    font-size: 1rem;
    color: #d6336c;
    font-weight: bold;
    margin: 5px 0;
  }

}

</style>
