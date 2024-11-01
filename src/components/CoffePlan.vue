<script setup>
import { defineProps, ref, defineEmits } from "vue";
const props = defineProps({
  name: {
    type: String,
    default: "Deafult Plan",
    validator(value) {
      return value.startsWith("The");
    },
  },
  selected: {
    type: Boolean,
    default: false,
  },
});
// const selected = ref(false);

const emit = defineEmits({
  selectedBox(payload) {
    return typeof payload === "string";
  },
});
const selectPlan = () => {
  emit("selectedBox", props.name);
};
</script>
<template>
  <div @click="selectPlan" class="plan" :class="{ 'active-plan': selected }">
    <div class="description">
      <span class="title"> {{ props.name }} </span>
    </div>
  </div>
</template>
