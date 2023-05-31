<template>
  <div>
    <h1>Vue クイズ</h1>
    <div class="app">
      <h2 class="quiz-title">Q. {{ currentQuestion.title }}</h2>
      <img class="quiz-image" :src="imagePath" alt="クイズタイトル" />
      <div class="container">
        <button
          v-for="(choice, index) in currentQuestion.answers"
          v-bind:key="index"
          v-on:click="answered(choice)"
        >
          {{ choice.text }}
        </button>
      </div>
      <div>{{ feedback }}</div>
      <button v-if="showNextButton" v-on:click="nextQuestion">
        次の問題へ
      </button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      feedback: "",
      currentQuestionIndex: 0,
      questions: [
        {
          title: "ひかるの出身は?",
          imagePath: "hikaru.jpg",
          answers: [
            {
              text: "山梨",
              isCorrect: true,
              feedback: "正解！",
            },
            {
              text: "山形",
              isCorrect: false,
              feedback: "残念！不正解！",
            },
            {
              text: "山口",
              isCorrect: false,
              feedback: "残念！不正解！",
            },
          ],
        },
        {
          title: "美咲が一番好きなのは?",
          imagePath: "misaki.jpg",
          answers: [
            {
              text: "白石麻衣",
              isCorrect: false,
              feedback: "残念！不正解！",
            },
            {
              text: "齋藤飛鳥",
              isCorrect: false,
              feedback: "残念！不正解！",
            },
            {
              text: "生田絵梨花",
              isCorrect: true,
              feedback: "正解！",
            },
          ],
        },
        {
          title: "まゆの最寄り駅は?",
          imagePath: "mayu.jpg",
          answers: [
            {
              text: "幕張本郷",
              isCorrect: false,
              feedback: "残念！不正解！",
            },
            {
              text: "海浜幕張",
              isCorrect: true,
              feedback: "正解！",
            },
            {
              text: "幕張豊砂",
              isCorrect: false,
              feedback: "残念！不正解！",
            },
          ],
        },
      ],
      showNextButton: false,
    }
  },
  methods: {
    answered(choice) {
      this.feedback = choice.feedback

      if (choice.isCorrect) {
        this.showNextButton = true
      }
    },
    nextQuestion() {
      this.currentQuestionIndex++
      this.feedback = ""
      this.showNextButton = false
    },
  },
  computed: {
    currentQuestion() {
      return this.questions[this.currentQuestionIndex]
    },
    imagePath() {
      return require("./images/" +
        this.questions[this.currentQuestionIndex].imagePath)
    },
  },
}
</script>

<style>
.app {
  display: flex;
  width: 100%;
  flex-direction: column;
  align-items: center;
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
}

.quiz-image {
  height: 300px;
  width: 300px;
  object-fit: contain;
}

.container {
  display: flex;
  height: 2em;
  width: 300px;
  padding: 1em;
  justify-content: space-around;
}
</style>
