<template>
  <div class="home">
    <QuestionCreator />
    <label
      ><span>Your question</span>
      <input type="text" v-model="question" placeholder="How was your day?" />
    </label>

    <div class="question-type">
      <span>Answer type</span>
      <label
        ><input
          type="radio"
          name="answer"
          v-model="answer"
          value="short"
        /><span>short text</span></label
      >
      <label
        ><input type="radio" name="answer" v-model="answer" value="long" /><span
          >long text</span
        ></label
      >
      <label
        ><input
          type="radio"
          name="answer"
          v-model="answer"
          value="single"
        /><span>one of multiple</span></label
      >
      <label
        ><input
          type="radio"
          name="answer"
          v-model="answer"
          value="multiple"
        /><span>multiple of multiple</span></label
      >
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref, watch } from "vue";
import QuestionCreator from "../components/QuestionCreator.vue";

export default defineComponent({
  name: "Home",
  components: { QuestionCreator },

  setup() {
    // const { question, shortText, longText, oneOfMultiple, multipleOfMultiple } =
    //   ref<string>("");
    const question = ref<string>("");
    const answer = ref<string>("");

    watch(
      () => [question.value, answer.value],
      (value) => {
        console.log(value);
      }
    );

    return { question, answer };
  },
});
</script>
