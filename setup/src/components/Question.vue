<!-- Question.vue -->
<template>
  <div class="question-container">
    <h2>{{ question.text }}</h2>
    <ul>
      <li v-for="answer in question.answers" :key="answer">
        <button @click="selectAnswer(answer)">{{ answer }}</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    question: Object
  },
  methods: {
    selectAnswer(answer) {
      this.$emit('answer', answer);
    }
  }
};
</script>

<style scoped>
.question-container {
  margin: 20px 0;
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

button {
  margin: 10px;
  padding: 10px 20px;
  border: none;
  border-radius: 5px;
  background-color: #007BFF;
  color: white;
  font-size: 16px;
  font-family: inherit;
  cursor: pointer;
  transition: background-color 0.3s;
}

button:hover {
  background-color: #0056b3;
}

@media (min-width: 768px) {
  .question-container {
    margin: 40px 0;
    padding: 40px;
  }
}

@media (min-width: 1024px) {
  .question-container {
    margin: 60px 0;
    padding: 60px;
  }

  button {
    margin: 15px;
    padding: 15px 30px;
    font-size: 18px;
  }
}
</style>
