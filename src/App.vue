<template>
  <div
    id="app"
    class="container"
  >
    <h1 class="display-3 text-center">Refresher</h1>
    <hr>
    <div class="row justify-content-sm-center">
      <question
        v-if="question"
        class="col-s6"
        :question="question"
      />
      <p v-else>No questions!</p>
    </div>
    <br>
    <div class="row justify-content-sm-center">
      <button
        v-if="question"
        class="btn btn-secondary"
        @click="nextQuestion"
      >
         Next
      </button>
    </div>
  </div>
</template>

<script>
import Question from "./Question"

const mockQuestions =  [
  {
    text: "What is love?",
    choices: ["Baby don't hurt me", "Baby don't hit me", "Hurt don't baby me"],
    rightChoiceIndex: 0
  },
  {
    text: "What is hate?",
    choices: ["Baby don't hurt me", "Baby don't hit me", "Hurt don't baby me"],
    rightChoiceIndex: 0
  }
]

export default {
  components: {
    Question
  },
  data: function() {
    return {
      questions: mockQuestions,
      question: mockQuestions[0],
      currentQuestionIndex: 0
    }
  },
  methods: {
    nextQuestion() {
      this.currentQuestionIndex++;
      this.question = this.questions[this.currentQuestionIndex]
    }
  }
}
</script>

<style>
</style>
