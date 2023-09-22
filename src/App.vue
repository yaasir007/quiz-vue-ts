<script setup lang="ts">
import { ref, computed } from "vue";

const quizCompleted = ref(false);
const currentQuestion = ref(0);


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
  let question = quizQuestions.question.
})

</script>

<template>
  <div class="quiz-section">
    <h1 class="title">Coding Quiz</h1>
    <div class="quiz-container">
      <div class="question">Which one is a programming language?</div>
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

        <div class="btns">
          <button>Cancel</button>
          <button>Submit</button>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped></style>
