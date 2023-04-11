<template>
  <div class="app">

    <h1>Would You Rather?</h1>

    <!-- bind props in child component to data in app.vue, and call method when receiving an answer-changed event from child -->
    <would-you-rather 
    v-bind:question="wyrQuestion"
    v-bind:answer1="wyrAnswer1"
    v-bind:answer2="wyrAnswer2"
    v-on:answer-changed="answerChanged">
    </would-you-rather>

    <p>{{ userSelectMessage }}</p>
  </div>
</template>

<script>
//import child component
import WouldYouRather from './components/WouldYouRather.vue'

export default {
  name: 'App',
  components: {
    WouldYouRather
  },
  data() {
    return {
      wyrQuestion: "Would you rather have the ability to see 10 minutes into the future or 150 years into the future?",
      wyrAnswer1: "10 minutes",
      wyrAnswer2: "150 years",
      userSelectMessage: ""
    }
  },
  methods: {
    answerChanged(choice) {
      this.userSelectMessage = "Thanks, you chose " + choice
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
