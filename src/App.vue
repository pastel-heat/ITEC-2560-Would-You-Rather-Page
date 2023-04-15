<template>
  <div class="app">

    <h1>Would You Rather?</h1>

    <!-- bind props in child components to data in app.vue, and call method when receiving an answer-changed event from child -->
    <would-you-rather v-for="wyr in questions"
    v-bind:id="wyr.id"
    v-bind:question="wyr.question"
    v-bind:answer1="wyr.answer1"
    v-bind:answer2="wyr.answer2"
    v-on:answer-changed="answerChanged">
    </would-you-rather>

    <answer-list v-bind:answers="answers"></answer-list>
  </div>
</template>

<script>
//import child components
import WouldYouRather from '@/components/WouldYouRather.vue'
import AnswerList from '@/components/AnswerList.vue'

export default {
  name: 'App',
  components: {
    WouldYouRather,
    AnswerList
  },
  data() {
    return {
      questions: [
        {
          id: 0,
          question: "Would you rather have the ability to see 10 minutes into the future or 150 years into the future?",
          answer1: "See 10 minutes into the future",
          answer2: "See 150 years into the future"
        },
        {
          id: 1,
          question: "Would you rather have telekinesis or telepathy?",
          answer1: "Have telekinesis",
          answer2: "Have telepathy"
        },
        {
          id: 2,
          question: "Would you rather be royalty 1000 years ago or be an average person today?",
          answer1: "Be royalty 1000 years ago",
          answer2: "Be an average person today"
        }
      ],
      answers: []
    }
  },
  methods: {
    answerChanged(choice, id) {
      // when receiving answer update from child, update the answers array using the id of the component as the index
      this.answers[id] = choice
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
