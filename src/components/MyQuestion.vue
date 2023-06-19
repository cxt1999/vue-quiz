<template>
  <QuestionItem
    v-for="questions in questionListProps"
    :key="questions.id"
    :questionProps="questions"
    @submit="submitQuestion"
  ></QuestionItem>
</template>
<script>
import QuestionItem from "./QuestionItem";

export default {
  name: "MyQuestion",
  props: ["questionListProps"],
  components: { QuestionItem },
  emits: { submitResult: null },
  setup(props, context) {
    const submitQuestion = (param1, param2) => {
      context.emit("submitResult", param1, param2);
    };
    return {
      submitQuestion,
    };
  },
};
</script>