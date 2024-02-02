<template>
    <div class="nav-buttons">
        <q-btn flat v-if="stepStore.step > 1" @click="stepStore.previousStep()" class="button prev-button">Go Back</q-btn>
        <q-btn v-if="stepStore.step < 4" @click="nextStep()" class="button next-button">Next Step</q-btn>
        <q-btn v-if="stepStore.step == 4" @click="stepStore.nextStep()" class="button confirm-button">Confirm</q-btn>
    </div>
</template>

<script setup>
import { useStepStore } from '../stores/step';
import { useUserStore } from '../stores/user';
import { usePriceStore } from '../stores/price';

const stepStore = useStepStore();
const userStore = useUserStore();
const priceStore = usePriceStore();

const nextStep = () => {
    if (stepStore.step == 1) {
        userStore.validateAll();
        if (userStore.errors.name || userStore.errors.email || userStore.errors.phoneNumber) {
            return;
        }
    }

    if (stepStore.step == 2) {
        if (!priceStore.validate()) {
            return;
        }
    }

    stepStore.nextStep();
};

</script>

<style scoped>
.nav-buttons {
    position: relative;
    bottom: 20px;
}

.button {
    position: absolute;
    border-radius: 8px;
    border: none;
    font-size: 16px;
    font-weight: 600;
    cursor: pointer;
    font-size: 18px;
}

.prev-button {
    background-color: transparent;
    color: var(--cool-gray);
    left: 0;
}

.prev-button:hover {
    color: var(--marine-blue);
}

.next-button {
    padding: 10px 32px;
    background-color: var(--marine-blue);
    color: var(--white);
    right: 0;
}

.next-button:hover {
    opacity: 0.8;
}

.confirm-button {
    padding: 10px 32px;
    background-color: var(--purplish-blue);
    color: var(--white);
    right: 0;
}

.confirm-button:hover {
    opacity: 0.8;
}
</style>