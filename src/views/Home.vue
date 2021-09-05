<template>
  <div class="home">
    <QuestionCreator />
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import QuestionCreator from "../components/QuestionCreator.vue";

export default defineComponent({
  name: "Home",
  components: { QuestionCreator },

  // setup() {
  //   // const { question, shortText, longText, oneOfMultiple, multipleOfMultiple } =
  //   //   ref<string>("");

  //   return { question, answer };
  // },
});
</script>
