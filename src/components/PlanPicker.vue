<script setup>
import { defineProps, ref, onMounted, onUnmounted } from "vue";
import CoffePlan from "./CoffePlan.vue";
const plans = ref(["The Single", "The Curious", "The HAcker"]);
const selectedCoffeePlan = ref("");

const handleSelectedCoffePlan = (name) => {
  selectedCoffeePlan.value = name;
};

const plansWrapper = ref();

onMounted(() => {
  console.log(plansWrapper.value);
});
</script>
<template>
  <div class="content">
    <h1 class="title">Coffee Plans</h1>

    <h2 ref="plansWrapper" class="subtitle">
      We travel the world to source the very best single origin coffee for you
    </h2>

    <div class="plans">
      {{ selectedCoffeePlan }}
      <CoffePlan
        v-for="plan in plans"
        :name="plan"
        :key="plan"
        :selected="plan === selectedCoffeePlan"
        @selectedBox="handleSelectedCoffePlan"
      />
    </div>
  </div>
</template>
