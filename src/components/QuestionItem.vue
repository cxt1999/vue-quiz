<template>
  <div class="questions-id">Question {{ questionProps.id }}</div>
  <div class="questions-question">{{ questionProps.question }}</div>
  <div v-for="(answer, key) in questionProps.answers" :key="key">
    <label>
      <input
        :name="questionProps.id"
        type="radio"
        @click="checkAnswer(key, questionProps.id)"
      />
      {{ key }}: {{ answer }}
    </label>
    <br />
  </div>
</template>

<script>
export default {
  name: "QuestionItem",
  props: ["questionProps"],
  emits: ["submit"],
  setup(props, context) {
    const checkAnswer = (key, id) => {
      if (key === props.questionProps.correctAnswer) {
        context.emit("submit", id, key === props.questionProps.correctAnswer);
      } else context.emit("submit", id, false);
    };
    return { checkAnswer };
  },
  // const counter = ref(0);
  // let accumulator = 0;
  //
  // const checkAnswer = (key) => {
  //   if (key === props.questionProps.correctAnswer) {
  //     if (accumulator === 0) {
  //       counter.value = props.myQuestionCountProps + 1;
  //     } else {
  //       counter.value = props.myQuestionCountProps;
  //     }
  //     context.emit("submit", counter.value);
  //     accumulator++;
  //   }
  // };
  // return {
  //   checkAnswer,
  // };
  // },
};
</script>

<style scoped>
.questions-question {
  border: solid black;
  border-radius: 12px;
  font-weight: 700;
  font-size: 22px;
  color: brown;
  margin: 2px;
  background-color: white;
}

.questions-id {
  margin-top: 20px;
  font-size: 20px;
  margin-left: 10px;
  font-weight: 600;
}
</style>
