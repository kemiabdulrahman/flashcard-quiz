<!-- Summary.vue -->
<template>
    <div class="summary-container">
      <h2>Quiz Summary</h2>
      <ul>
        <li v-for="(question, index) in questions" :key="index">
          <p>{{ question.text }}</p>
          <p>Your Answer: <span :class="{'correct': userAnswers[index] === question.correctAnswer, 'incorrect': userAnswers[index] !== question.correctAnswer}">{{ userAnswers[index] }}</span></p>
          <p>Correct Answer: {{ question.correctAnswer }}</p>
        </li>
      </ul>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      questions: Array,
      userAnswers: Array
    }
  };
  </script>
  
  <style scoped>
  .summary-container {
    margin: 20px;
    padding: 20px;
    border: 1px solid #ddd;
    border-radius: 8px;
    background-color: #f9f9f9;
  }
  
  ul {
    list-style-type: none;
    padding: 0;
  }
  
  li {
    margin: 10px 0;
  }
  
  .correct {
    color: green;
    font-weight: bold;
  }
  
  .incorrect {
    color: red;
    font-weight: bold;
  }
  
  @media (min-width: 768px) {
    .summary-container {
      margin: 40px;
      padding: 40px;
    }
  }
  
  @media (min-width: 1024px) {
    .summary-container {
      margin: 60px;
      padding: 60px;
    }
  }
  </style>
  