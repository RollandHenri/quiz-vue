<script setup>
import { onMounted, ref } from "vue";
import Quiz from "./components/Quiz.vue";

const quiz = ref(null);
const state = ref("loading");

onMounted(() => {
  fetch("/quiz.json")
    .then((r) => {
      if (r.ok) {
        return r.json();
      }
      throw new Error("Impossible de charger le JSON");
    })
    .then((data) => {
      quiz.value = data;
      state.value = "idle";
    })
    .catch((e) => {
      state.value = "error";
    });
});
</script>

<template>
  <h1>Quiz Vue.js</h1>
  <div v-if="state === 'error'">
    <p>Impossible de charger le quiz</p>
  </div>

  <div :aria-busy="state === 'loading'">
    <Quiz :quiz="quiz" v-if="quiz" />
  </div>
</template>

<style scoped>
h1 {
  text-align: center;
  margin: 2rem;
}
</style>
