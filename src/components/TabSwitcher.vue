<script setup>
import { ref } from 'vue';

// Subscription type by default
const isActive = ref(1);

// Setting all types of subscription as tabs
const tabs = [
   { id: 1, name: 'Registration' },
   { id: 2, name: 'Renewal' },
   { id: 3, name: 'Transfer' }
]

const emit = defineEmits(['activateSubscription'])

// Sending a new subscription type by 'click' and switching to the corresponding tab
const chooseSubscription = (id, name) => {
   isActive.value = id;
   emit('activateSubscription', name)
}
</script>



<template>
   <div
      class="plan__tabs tabs flex justify-between max-w-[800px] mx-auto p-[10px] border border-solid border-graphite rounded-[50px] font-inter font-medium">
      <span v-for="tab in tabs" :key="tab.id" :class="{ active: isActive === tab.id }" @click="chooseSubscription(tab.id, tab.name)">LEI {{
         tab.name }}</span>
   </div>
</template>



<style scoped>
.tabs>span {
   padding: 12px 30px;
   border-radius: 30px;
   transition: 0.3s;
}

.tabs>span {
   cursor: pointer;
}

.tabs>span.active,
.tabs>span.active:hover {
   background: rgba(206, 17, 35, 1);
}

.tabs>span:hover {
   background: rgba(206, 17, 35, .4);
}
</style>