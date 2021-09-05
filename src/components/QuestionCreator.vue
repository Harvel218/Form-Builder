<template>
  <section class="question">
    <label
      ><span>Your question</span>
      <input type="text" v-model="question" placeholder="How was your day?" />
    </label>

    <div class="question__type">
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
      <div v-if="answer === 'single' || answer === 'multiple'">
        <input
          placeholder="great"
          type="text"
          name="answerContent"
          v-model="answerContent"
          @keyup.enter="addAnswer(answerContent)"
        /><button type="button" @click="addAnswer(answerContent)">
          Add answer
        </button>
      </div>
    </div>
    <p v-if="question">{{ question }}</p>
    <div class="question__insights" v-if="answer">
      <div v-if="answer === 'short'">
        <input
          type="text"
          placeholder="My answer - max 100 characters"
          maxlength="100"
        />
      </div>
      <div v-else-if="answer === 'long'">
        <textarea
          placeholder="My longer answer - max 500 characters"
          maxlength="500"
        ></textarea>
      </div>
      <div v-else-if="answer === 'single'">
        <label v-for="answer in radioAnswers" :key="answer.index">
          <input type="checkbox" :name="question" />
          {{ answer }}
        </label>
      </div>
      <div v-else-if="answer === 'multiple'">
        <label v-for="answer in radioAnswers" :key="answer.index">
          <input type="radio" :name="question" />
          {{ answer }}
        </label>
      </div>
    </div>
  </section>
</template>
<script lang="ts">
import { defineComponent, ref, watch } from "vue";

export default defineComponent({
  setup() {
    const question = ref<string>("");
    const answer = ref<string>("");
    const answerContent = ref<string>("");
    const radioAnswers = ref<string[]>([]);

    const addAnswer = (value: string) => {
      radioAnswers.value.push(value);
      console.log(radioAnswers.value);
    };

    watch(
      () => [question.value, answer.value],
      (value) => {
        console.log(value);
      }
    );

    return { question, answer, answerContent, addAnswer, radioAnswers };
  },
});
</script>
<style lang="scss" scoped>
</style>