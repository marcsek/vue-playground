<script setup>
import { onMounted, ref } from 'vue';
import data from './Questions.js';

const listData = ref(data);

const getStatusClass = status => {
  status = status.toLowerCase();

  if (status === 'partially_correct') return status.replace('_', '-');
  return status;
};
</script>

<template>
  <section id="wrapper">
    <div class="category" v-for="(questions, category) in listData" key="category">
      {{ category }}
      <div class="question" v-for="question in questions" key="question">
        <div :class="`status ${getStatusClass(question.status)}`"></div>
        <h3>{{ question.name }}</h3>
      </div>
    </div>
  </section>
</template>

<style scoped>
.category {
  flex-grow: 1;
  display: flex;
  flex-direction: column;
  gap: 12px;
}

#wrapper {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
}

.question {
  display: flex;
  align-items: center;
  gap: 4px;
  background-color: white;
  padding: 10px;
  border-right: 25px solid #11967e;
  border-radius: 4px;
  box-shadow: rgba(0, 0, 0, 20%) 0px 1px 2px;
}

.status {
  width: 20px;
  height: 20px;
  border-radius: 50%;
}

.unattempted {
  background-color: transparent;
  border: 1px solid #6772e54d;
}

.incorrect {
  background-color: red;
}
.correct {
  background-color: green;
}

.partially-correct {
  background-color: yellow;
}
</style>
