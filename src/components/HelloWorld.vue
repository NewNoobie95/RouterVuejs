<template>
  <div class="hello">
    <h1 v-if="show">{{ msg }}</h1>
    <p>{{ quiz.title }}</p>

    <div v-for="(question, index) in quiz.questions" v-bind:key="question.id">
      <div v-show="index === questionIndex">
        <h4>{{ question.text }}</h4>
        <ol>
          <li v-for="response in question.responses" v-bind:key="response.id">
            <label>
              <input type="radio"
                     v-bind:value="response.choice"
                     v-bind:name="index"
                     v-model="picked"> {{ response.text }}
            </label>
          </li>
        </ol>

        <button v-on:click="check(question.correct, picked)">
          <span v-if="questionIndex == quiz.questions.length - 1">Finish</span>
          <span v-else>Next</span>
        </button>

        <h5>Correct Answer : {{ totalCorrect }}</h5>
      </div>
    </div>

    <div v-show="questionIndex == quiz.questions.length">
      <h2>End of Quiz</h2>
      <p>Correct Answer : {{ totalCorrect }} / {{ quiz.questions.length }}</p>
      <p>Score : {{ scoreCal() }}</p>
    </div>
  </div>
</template>

<script>
var quiz = {
    title: 'Quizes',
    questions: [
      {
        text: "How many planets in our Solar System?",
        responses: [
          { text: '8', choice: 'A' },
          { text: '9', choice: 'B' },
          { text: '8', choice: 'C' },
          { text: '7', choice: 'D' }
        ],
        correct: 'A'
      },
      {
        text: "What is the hottest planet in our Solar System?",
        responses: [
          { text: 'Mercury', choice: 'A' },
          { text: 'Mars', choice: 'B' },
          { text: 'Sun', choice: 'C' },
          { text: 'Venus', choice: 'D' }
        ],
        correct: 'D'
      },
      {
        text: "What is the farthest planet in our Solar System?",
        responses: [
          { text: 'Uranus', choice: 'A' },
          { text: 'Neptune', choice: 'B' },
          { text: 'Pluto', choice: 'C' },
          { text: 'VG2019', choice: 'D' }
        ],
        correct: 'A'
      },
      {
        text: "How many Asteroid Belt in the habitable zone?",
        responses: [
          { text: '1', choice: 'A' },
          { text: '3', choice: 'B' },
          { text: '2', choice: 'C' },
          { text: 'None', choice: 'D' }
        ],
        correct: 'C'
      },
      {
        text: "What is the closest solar system to our solar system?",
        responses: [
          { text: 'Kepler', choice: 'A' },
          { text: 'Sirius B', choice: 'B' },
          { text: 'Alpha Centauri', choice: 'C' },
          { text: 'Sirius A', choice: 'D' }
        ],
        correct: 'C'
      }
    ]
  };

export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data: function() {
    return {
      picked: '',
      show: true,
      quiz: quiz,
      questionIndex: 0,
      totalCorrect: 0,
      userResponses: Array(quiz.questions.length).fill(false)
    }
  },
  methods: {
    check(correct, picked) {
      if (correct === picked) this.totalCorrect++;
      this.questionIndex++;
    },
    scoreCal: function() {
      return (100 / quiz.questions.length) * this.totalCorrect;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
