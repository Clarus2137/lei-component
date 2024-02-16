<script setup>
import TabSwitcher from './TabSwitcher.vue';
import AllPlans from './AllPlans.vue'
import CompleteOrder from './CompleteOrder.vue';
import ConfirmOrder from './ConfirmOrder.vue';
import { ref } from 'vue';

// Subscription type by default
const currentSubscriptionType = ref('Registration');

// Method calling by custom event "activateSubscription";
// subscriptionType is equal "name" from "chooseSubscription" event of TabSwitcher
const getSubscription = (subscriptionType) => {
  // Updating of current subscribtion type
  currentSubscriptionType.value = subscriptionType;
}
</script>



<template>
   <div class="plan pt-[100px] pb-[55px] text-light font-inter">
      <div class="plan__wrapper container">
         <TabSwitcher @activateSubscription="getSubscription" />
         <AllPlans :currentSubscriptionType="currentSubscriptionType" />
      </div>
   </div>
   <div class="form pt-[120px] pb-[55px]">
      <div class="form-wrapper container">
         <CompleteOrder :currentSubscriptionType="currentSubscriptionType" />
      </div>
   </div>
   <div class="confirm pt-[100px] pb-[55px] text-light font-inter">
      <div class="confirm-wrapper container text-center">
         <ConfirmOrder />
      </div>
   </div>
</template>



<style scoped>
.plan {
   background: url("./../assets/img/plan-bg.jpg") no-repeat;
   background-size: cover;
}

.confirm {
   background: url("./../assets/img/confirm-bg.jpg") no-repeat;
   background-size: cover;
}
</style>