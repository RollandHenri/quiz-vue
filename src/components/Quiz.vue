<script setup>
defineProps({
  quiz: {
    quiz: Object,
  },
});
</script>

<template>
  <div>
    <h2>
      {{ quiz.title }}
    </h2>
  </div>
</template>

<style scoped>
h2 {
  text-align: center;
  margin-bottom: 2rem;
}
</style>
