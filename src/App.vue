<script setup lang="ts">
import { ref, computed } from "vue";

const quizCompleted = ref(false);
const currentQuestion = ref(0);
const selected = ref();


const quizQuestions = [
  {
    question: "Javascript is a programming language",
    options: ["True", "False", "Not know", "Maybe"],
    answer: 1,
    selected: null,
  },
  {
    question: "Python is a programming language",
    options: ["True", "False", "Not know", "Maybe"],
    answer: 2,
    selected: null,
  },
  {
    question: "Ruby is a programming language",
    options: ["True", "False", "Not know", "Maybe"],
    answer: 3,
    selected: null,
  },
];

const score = computed(() => {
  let value = 0;
  quizQuestions.map((question) => {
    if (question.selected == question.answer) {
      value++;
    }
    return value;
  }) 
})

const getCurrentQuestion = computed(() => {
  let question = quizQuestions[currentQuestion.value]
  // question.index = currentQuestion.value
  return question;
})

// const setAnswer = (event) => {
//   quizQuestions.value[currentQuestion.value].selected = event.target.value;
//   event.target.value = null;
// }

const nextQuestion = () => {
  if (currentQuestion.value < quizQuestions.length - 1) {
    currentQuestion.value++;
  } else {
    quizCompleted.value = true;
  }
}

const resetQuiz = () => {
  currentQuestion.value = 0;
}

</script>

<template>
  <div class="quiz-section">
    <h1 class="title">Coding Quiz</h1>
    <div class="quiz-container">
      <div class="question">{{ getCurrentQuestion.question }}</div>
      <div class="answers">
        <div class="option">
          <input type="radio" name="Name1" label="Hello" class="radio-btn" />
          <p>JavaScript</p>
        </div>
        <div class="option">
          <input type="radio" name="Name1" label="Hello" class="radio-btn" />
          <p>Ruby</p>
        </div>
        <div class="option">
          <input type="radio" name="Name1" label="Hello" class="radio-btn" />
          <p>HTML</p>
        </div>
        <div class="option">
          <input type="radio" name="Name1" label="Hello" class="radio-btn" />
          <p>CSS</p>
        </div>

        <div class="score">
          <span>3/5</span>
        </div>

        <div class="btns">
          <button @click="resetQuiz">Reset</button>
          <button @click="nextQuestion">Next</button>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped></style>
