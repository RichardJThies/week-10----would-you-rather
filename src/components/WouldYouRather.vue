<template>
  <div class="wyr">
    <h2>Please make your choice.</h2>

    <h3>{{question}}</h3>

    <input type="radio" v-model="choice" v-bind:value="answer1" v-on:change="choiceMade"> <!--needs v-bind because a radio buttob doesn't have a value by default, it starts empty. v-bind sets the values-->
    <label>{{answer1}}</label>

    <input type="radio" v-model="choice" v-bind:value="answer2" v-on:change="choiceMade"> <!--v-on change calls a method to send a message to parent component-->
    <label>{{answer2}}</label>
  </div>
</template>

<script>
export default {
  name: 'WouldYouRather',
  props: { // data received from parent components is stored in prop values. "data()" is generated/managed by components for internal use
    question: String, // defining props works by putting a type (String), rather than a value
    answer1: String, // Child component (which has the props) does not modify "question", answer1", or "answer2". Create new data function instead.
    answer2: String
  },
  data() { // data() is what WouldYouRather.vue is generating itself, rather than receivng from parent component. It figures out what the radio buttion input choice is
    return { // returns object
      choice: ''
    }
  },
  methods: {
    choiceMade() {
      this.$emit('answer-changed', this.choice) // data can be sent with event to the parent
      // ^^$emit is a Vue method to send a message/event to parent component. Name can be anything (don't use  built-in JS names such as click/change) name with ''-'' will always be valid
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
  color: aqua;
}
.wyr {
  border: 3px red solid;
  background: bisque;
  margin: 20px;
}

</style>
