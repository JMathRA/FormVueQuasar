<template>
    <div class="sidebar">
        <StepComponent v-for="step in steps" :key="step.number" :step="step" :active="step.number == stepStore.step" />
    </div>
</template>

<script setup>
import { useStepStore } from '../stores/step';
import StepComponent from '../components/StepComponent.vue';

const stepStore = useStepStore()

let steps = [
    {
        number: 1,
        label: "YOUR INFO"
    },
    {
        number: 2,
        label: "SELECT PLAN"
    },
    {
        number: 3,
        label: "ADD-ONS"
    },
    {
        number: 4,
        label: "SUMMARY"
    }
];

</script>

<style scoped>
.sidebar {
    height: 100%;
    width: 320px;
    padding: 60px 40px;
    background: url("../assets/images/bg-sidebar-desktop.svg");
    background-size: cover;
    border-radius: 16px;
}
</style>