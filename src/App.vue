<template>
  <MyQuestion :questionListProps="questionsList" @submitResult="getResult" />
  <button @click="submitResult">Result</button>
</template>

<script>
import MyQuestion from "./components/MyQuestion";
import { ref } from "vue";

export default {
  name: "App",
  components: { MyQuestion },
  setup() {
    const questionsList = ref([
      {
        id: 1,
        question:
          "  Which of the following is correct about features of JavaScript?",
        answers: {
          a: "JavaScript is a lightweight, interpreted programming language.",
          b: "JavaScript is designed for creating network-centric applications.",
          c: "All of the above.",
        },
        correctAnswer: "a",
        choice: "",
      },
      {
        id: 2,
        question:
          "  Which built-in method calls a function for each element in the array?",
        answers: {
          a: "while().",
          b: "loop().",
          c: "forEach().",
        },
        correctAnswer: "b",
        choice: "",
      },
      {
        id: 3,
        question: "  Which of the following code creates an object?",
        answers: {
          a: "var book = Object();",
          b: "var book = new OBJECT();",
          c: "var book = new Object();",
        },
        correctAnswer: "c",
        choice: "",
      },
    ]);
    const getResult = function (id, bool) {
      for (let i = 0; i < questionsList.value.length; i++) {
        if (questionsList.value[i].id === id) {
          questionsList.value[i].choice = bool;
        }
      }
    };

    const submitResult = function () {
      let accumulator = 0;
      for (let i = 0; i < questionsList.value.length; i++) {
        if (questionsList.value[i].choice === true) accumulator++;
      }
      alert(`Your score: ${accumulator} / ${questionsList.value.length}`);
    };
    return { questionsList, submitResult, getResult };
  },
};
</script>

<style scoped>
button {
  padding: 10px 30px;
  border: 2px solid black;
  border-radius: 10px;
  font-size: 16px;
  /* margin: 20px auto; */
  top: 10px;
  right: 50%;
  position: fixed;
  font-weight: 550;
  background-color: rgb(228, 102, 102);
}

button:hover {
  background-color: rgb(162, 162, 162);
  color: white;
}
</style>