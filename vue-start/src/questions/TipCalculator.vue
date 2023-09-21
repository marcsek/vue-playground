<script setup>
import { ref, computed } from 'vue';

const formState = ref({ bill: 50, tipPercentage: 18, nOfPeople: 1 });

const totalTipComputed = computed(() => {
  const { value: state } = formState;
  const tip = state.bill * (state.tipPercentage / 100);
  return `$${tip.toFixed(2)}`;
});

const tipPerPersonComputed = computed(() => {
  const { value: state } = formState;
  const tip = state.bill * (state.tipPercentage / 100);
  if (state.nOfPeople <= 0) return '-';
  return `$${(tip / state.nOfPeople).toFixed(2)}`;
});
</script>

<template>
  <section>
    <form>
      <label>
        Bill
        <input v-model="formState.bill" min="0" type="number" />
      </label>
      <label>
        Tip Percentage
        <input v-model="formState.tipPercentage" min="0" type="number" />
      </label>
      <label>
        Number of People
        <input v-model="formState.nOfPeople" min="0" type="number" />
      </label>
    </form>
    <p>Total Tip: {{ totalTipComputed }}</p>
    <p>Tip Per Person: {{ tipPerPersonComputed }}</p>
  </section>
</template>

<style scoped>
section {
  background-color: lightgrey;
  width: fit-content;
  padding: 10px;
  border-radius: 10px;
}

input {
  display: block;
}

form {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}
</style>
