<template>
  <h1>Vue クイズ</h1>
  <div class="app">
    <h2 class="quiz-title">Q. {{ questions.title }}</h2>
    <img
      class="quiz-image"
      src="https://via.placeholder.com/300x300"
      alt="クイズタイトル"
    />
    <div class="container">
      <button
        v-for="(choice, i) in question.answers"
        v-bind:key="i"
        v-on:click="answered(answer)"
      >
        {{ answer.text }}
      </button>
    </div>
    <div>{{ feedback }}</div>
    <button v-if="true">次の問題へ</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      feedback: "",
      questions: [
        {
          title:"ひかるの出身は?",
          answers:[
            {
            text:"山梨",
            isCorrect: true,
            feedback:"正解！"
            },{
            text:"山形",
            isCorrect: false,
            feedback:"残念！不正解！"
            },{
            text:"山口",
            isCorrect: false,
            feedback:"残念！不正解！"
            }]


        },
        {
          title:"美咲が一番好きなのは?",
          answers:[
            {
            text:"白石麻衣",
            isCorrect: false,
            feedback:"残念！不正解！"
            },{
            text:"齋藤飛鳥",
            isCorrect: false,
            feedback:"残念！不正解！"
            },{
            text:"生田絵梨花",
            isCorrect: true,
            feedback:"正解！"
            }]


        },
        {
          title:"まゆの最寄り駅は?",
          answers:[
            {
            text:"幕張本郷",
            isCorrect: false,
            feedback:"残念！不正解！"
            },{
            text:"海浜幕張",
            isCorrect: true,
            feedback:"正解！"
            },{
            text:"幕張豊砂",
            isCorrect: false,
            feedback:"残念！不正解！"
            }]


        },

      ]
  },
  methods:{
    answered(answeer){
      this.feedback = answer.feedback

      if(answer.isCorrect){

      }
    }
  },
},
computed:{
  questionUmagePath(){
    return "./images/" + this.quiz.image
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
