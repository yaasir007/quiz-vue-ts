<script setup lang="ts">
import { ref } from "vue";
const answer = ref(true);

const quiz = [
  {
    question: "Im too good",
    options: []
  }
]

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
