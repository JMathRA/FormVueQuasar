<template>
  <div class="container">
    <TheSideBar />
    <ContentView>
      <YourInfo v-if="stepStore.step == 1" />
      <SelectPlan v-if="stepStore.step == 2" />
      <AddOns v-if="stepStore.step == 3" />
      <SummaryApp v-if="stepStore.step == 4" />
      <ThankYou v-if="stepStore.step == 5" />
    </ContentView>
  </div>
</template>

<script setup>
  import { useStepStore } from './stores/step';
  import ContentView from './components/ContentView.vue';
  import ThankYou from './components/ThankYou.vue';
  import SummaryApp from './components/SummaryApp.vue';
  import AddOns from './components/AddOns.vue';
  import SelectPlan from './components/SelectPlan.vue';
  import YourInfo from './components/YourInfo.vue';
  import TheSideBar from './components/TheSideBar.vue';

  const stepStore = useStepStore();

</script>

<style scoped>
.container {
  width: 1080px;
  height: 720px;
  background-color: var(--alabaster);
  border-radius: 16px;
  padding: 20px;
  box-shadow: 0px 0px 20px 0px rgba(0, 0, 0, 0.3);
  display: flex;
}
</style>