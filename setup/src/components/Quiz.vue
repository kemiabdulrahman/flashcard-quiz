<!-- QuizComponent.vue -->
<template>
  <div class="quiz-container">
    <h1>Quiz Competition</h1>
    <Timer :time="time" @time-up="handleTimeUp"/>
    <Question
      v-if="currentQuestionIndex < questions.length"
      :question="questions[currentQuestionIndex]"
      @answer="handleAnswer"
    />
    <div v-else>
      <h2>Quiz Over!</h2>
      <p>Your Score: {{ score }}</p>
      <Summary :questions="questions" :user-answers="userAnswers" />
    </div>
  </div>
</template>

<script>
import Question from './Question.vue';
import Timer from './Timer.vue';
import Summary from './Summary.vue';

export default {
  components: {
    Question,
    Timer,
    Summary
  },
  data() {
    return {
      currentQuestionIndex: 0,
      score: 0,
      time: 10, // countdown time in seconds
      userAnswers: [],
      questions: [
        { text: 'What is the capital of France?', answers: ['Paris', 'London', 'Rome'], correctAnswer: 'Paris' },
        { text: 'What is 2 + 2?', answers: ['3', '4', '5'], correctAnswer: '4' },
        { text: 'Which planet is known as the Red Planet?', answers: ['Earth', 'Mars', 'Jupiter'], correctAnswer: 'Mars' },
        { text: 'Who wrote "To be, or not to be"?', answers: ['Shakespeare', 'Hemingway', 'Tolkien'], correctAnswer: 'Shakespeare' },
        { text: 'What is the speed of light?', answers: ['300,000 km/s', '150,000 km/s', '75,000 km/s'], correctAnswer: '300,000 km/s' },
        { text: 'What is the chemical symbol for water?', answers: ['H2O', 'O2', 'CO2'], correctAnswer: 'H2O' },
        { text: 'Who painted the Mona Lisa?', answers: ['Van Gogh', 'Picasso', 'Da Vinci'], correctAnswer: 'Da Vinci' },
        { text: 'What is the largest mammal?', answers: ['Elephant', 'Blue Whale', 'Giraffe'], correctAnswer: 'Blue Whale' },
      ]
    };
  },
  methods: {
    handleAnswer(answer) {
      if (answer === this.questions[this.currentQuestionIndex].correctAnswer) {
        this.score++;
      }
      this.currentQuestionIndex++;
    },
    handleTimeUp() {
      this.currentQuestionIndex = this.questions.length; // end the quiz when time is up
    }
  }
};
</script>

<style scoped>
.quiz-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 20px;
  margin: 0 auto;
  max-width: 600px;
  text-align: center;
  border-radius: 10px;
}

h1 {
  color: #333;
}

h2 {
  color: #555;
}

p {
  font-size: 18px;
  color: #666;
}

@media (min-width: 768px) {
  .quiz-container {
    max-width: 80%;
  }
}

@media (min-width: 1024px) {
  .quiz-container {
    max-width: 60%;
  }
}
</style>
