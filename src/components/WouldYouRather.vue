<template>
  <div class="wyr">
    
    <h2>{{ question }}</h2>

    <!-- radio buttons bound to wyr answers, and modeled to choice in data-->
    <input type="radio" v-model="choice" v-bind:value="answer1" v-on:change="choiceMade">
    <label>{{ answer1 }}</label>

    <input type="radio" v-model="choice" v-bind:value="answer2" v-on:change="choiceMade">
    <label>{{ answer2 }}</label>
  </div>
</template>

<script>
export default {
  name: 'WouldYouRather',
  props: {
    id: Number,
    question: String,
    answer1: String,
    answer2: String
  },
  data() {
    return {
      choice: ''
    }
  },
  methods: {
    choiceMade() {
      //send event to parent when radio button selection is changed. include current choice w/ event
      this.$emit('answer-changed', this.choice, this.id)
    }
  }  
}
</script>

<style scoped>
h3 {
  margin: 40px 0 0;
}

.wyr {
  border: 2px solid black;
  background-color: skyblue;
  color: black;
}


</style>
