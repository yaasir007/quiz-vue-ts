<script setup lang="ts">
import { ref, computed } from "vue";

const quizCompleted = ref(false);
const currentQuestion = ref(0);
const quizScore = ref(0);

const quizQuestions = [
  {
    question: "Javascript is a programming language",
    options: ["True", "False", "Not know", "Maybe"],
    answer: 1,
    selected: null,
  },
  {
    question: "Python is a programming language",
    options: ["True", "Fale", "Not know", "Maybe"],
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
  quizQuestions.map((question) => {
    if (question.selected == question.answer) {
      quizScore++;
    }
    return quizScore;
  });
});

const getCurrentQuestion = computed(() => {
  let question = quizQuestions[currentQuestion.value];
  question.index = currentQuestion.value
  return question;
});

const setAnswer = (event) => {
  quizQuestions[currentQuestion.value].selected = event.target.value;
  event.target.value = null;
};

const nextQuestion = () => {
  if (currentQuestion.value < quizQuestions.length - 1) {
    currentQuestion.value++;
  } else {
    quizCompleted.value = true;
  }
};

const resetQuiz = () => {
  currentQuestion.value = 0;
};
</script>

<template>
  <div class="quiz-section">
    <h1 class="title">Coding Quiz</h1>
    <div class="quiz-container">
      <div class="question">{{ getCurrentQuestion.question }}</div>
      <div class="answers">
        <div
          v-for="(option, index) in getCurrentQuestion.options"
          :key="index"
          class="option"
        >
          <input type="radio" name="Name1" label="Hello" class="radio-btn" />
          <p>{{ option }}</p>
        </div>

        <div class="score">
          <span>{{ quizScore }} / {{ quizQuestions.length }}</span>
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
