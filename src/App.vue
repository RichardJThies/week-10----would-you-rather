<template>
  <div id="app"> <!--template tag contain only 1 child element, aka the div. Put everything in the div if you need things in the template.-->
    <h1>Would you rather...?</h1>

    <would-you-rather v-bind:question="wyrQuestion"
    v-bind:answer1="wyrAnswer1"
    v-bind:answer2="wyrAnswer2"
    v-on:answer-changed="answerChanged"> <!--connects the data to the props. AnswerChange calls method to receive event/message from child component-->
      
    </would-you-rather> <!--Must reference other components in the template in order to use their elements. Could also use WouldYouRather instead, and the reference would still work.-->
    <label>{{userSelectionMessage}}</label>


  </div>
</template>

<script>
import WouldYouRather from './components/WouldYouRather.vue'

export default {
  name: 'App',
  components: {
    WouldYouRather
  },
  data() { // data is being sent to WouldYouRather component, as it is the child component
    return {
      wyrQuestion : "Would you rather dance or sing?",
      wyrAnswer1: "Dance",
      wyrAnswer2: "Sing",
      userSelectionMessage: "" // empty string as no choice has been made yet
    }
  },
  methods: {
    answerChanged(choice) { //recieves the data from the event sent by the child component
      this.userSelectionMessage = `Thanks! You have chosen to ${choice.toLowerCase()}.` //updates userSelectionMessage
    }
  }
}
</script>

<style>

body {
  background: lightslategray;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  background: lightgoldenrodyellow
}
</style>
