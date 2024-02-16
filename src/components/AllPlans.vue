<script setup>
import { ref, computed } from 'vue';
import { subscriptionOptions } from './plans.js';


// Getting of the current subscription type from SelectPlan and setting it as a prop
const props = defineProps({
   currentSubscriptionType: String
});

// Searching of the subscription object from plans.js matching the current subscription type from props.
const currentSubscription = computed(() => {
   return subscriptionOptions.find(option => option.name === props.currentSubscriptionType) || {};
});

// Set plans for the current subscription type
const plans = computed(() => currentSubscription.value.plans || []);

// Set a plan name to the title
const planName = computed(() => currentSubscription.value.name || '');

// Set a plan by default
const isChosen = ref(2);
</script>

<template>
   <div class="plan__reg reg flex flex-wrap justify-center gap-y-20 mt-[100px]">
      <div class="plan__title">
         <p class="headline font-axiforma font-semibold text-[45px] text-center">Select {{ planName }} plan</p>
         <p class="tagline text-xl text-center">Please choose the plan that suits you best</p>
      </div>
      <div class="plan__items w-full flex justify-center gap-x-[60px]">

         <div v-for="plan in plans" :key="plan.id" class="plan__item w-full max-w-[380px] pt-10 px-10 pb-[50px] rounded-[1.125rem] duration-300"
            :class="{ popular: plan.isPopular, active: isChosen === plan.id }" @click="isChosen = plan.id">
            <div class="plan__card card flex flex-wrap gap-y-10">
               <p class="card__title w-full pt-[15px] font-semibold text-[1.5625rem] leading-[1] uppercase">{{ plan.name }}</p>
               <div class="card__price w-full text-[1.125rem] leading-[1] text-darkgray">
                  <p><span class="price text-light text-[1.875rem] leading-[1] font-medium">{{ plan.price }}&#163;</span> / {{ plan.years }} year(s)</p>
                  <p class="mt-[10px]">{{ Number((plan.price / plan.years).toFixed(2)) }}&#163; per 1 year</p>
               </div>
               <div class="card__benefits benefits w-full">
                  <div v-for="benefit in plan.benefits" :key="benefit.id" class="benefits__item py-[15px] text-[1.125rem] leading-[1.2] font-extralight">
                     <p class="flex gap-x-[15px]">
                        <svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
                           <path
                              d="M9.99999 18.3333C14.6024 18.3333 18.3333 14.6023 18.3333 9.99996C18.3333 5.39759 14.6024 1.66663 9.99999 1.66663C5.39762 1.66663 1.66666 5.39759 1.66666 9.99996C1.66666 14.6023 5.39762 18.3333 9.99999 18.3333Z"
                              fill="#FAFAFA" />
                           <path d="M7.5 10L9.16667 11.6667L12.5 8.33337" stroke="black" stroke-width="1.5"
                              stroke-linecap="round" stroke-linejoin="round" />
                        </svg>
                        <span>{{ benefit.content }}</span>
                     </p>
                  </div>
               </div>
               <button type="button" class="card__btn w-fit mx-auto py-[11px] px-6 bg-light border border-solid border-white text-black rounded-[30px] text-[0.9375rem] leading-[1] capitalize duration-300 hover:bg-transparent hover:text-white">Chose a plan</button>
            </div>
         </div>
      </div>
      <div class="arrow-down text-center">
         <button class="arrow-down__btn" type="button">
            <span>Continue placing your order</span>
            <svg class="mt-[15px] mx-auto" width="30" height="30" viewBox="0 0 30 30" fill="none"
               xmlns="http://www.w3.org/2000/svg">
               <path
                  d="M1.4031e-07 15C1.4031e-07 17.9667 0.879735 20.8668 2.52796 23.3335C4.17618 25.8003 6.51885 27.7229 9.25975 28.8582C12.0006 29.9935 15.0166 30.2906 17.9263 29.7118C20.8361 29.133 23.5088 27.7044 25.6066 25.6066C27.7044 23.5088 29.133 20.8361 29.7118 17.9263C30.2906 15.0166 29.9935 12.0006 28.8582 9.25975C27.7229 6.51885 25.8003 4.17618 23.3335 2.52796C20.8668 0.879735 17.9667 1.4031e-07 15 1.4031e-07C13.0301 -0.000269303 11.0794 0.387533 9.25943 1.14126C7.43942 1.89498 5.78573 2.99986 4.3928 4.3928C2.99986 5.78573 1.89498 7.43942 1.14126 9.25943C0.387533 11.0794 -0.000269303 13.0301 1.4031e-07 15ZM20.8461 11.8697C21.1079 11.6097 21.4618 11.4637 21.8308 11.4637C22.1997 11.4637 22.5537 11.6097 22.8154 11.8697C22.9443 11.9983 23.0464 12.1511 23.1158 12.3194C23.1852 12.4878 23.2204 12.6682 23.2195 12.8503C23.2189 13.2208 23.0714 13.576 22.8092 13.8379L16.0092 20.6164C15.7453 20.8571 15.3988 20.9869 15.0416 20.9789C14.6845 20.9709 14.3442 20.8256 14.0913 20.5733L7.18974 13.6933C7.06044 13.564 6.95787 13.4105 6.88789 13.2416C6.81792 13.0726 6.7819 12.8916 6.7819 12.7087C6.7819 12.3394 6.92861 11.9852 7.18974 11.7241C7.45088 11.463 7.80505 11.3163 8.17436 11.3163C8.54366 11.3163 8.89784 11.463 9.15897 11.7241L15.0051 17.6308L20.8461 11.8697Z"
                  fill="white" />
            </svg>
         </button>
      </div>
   </div>
</template>



<style scoped>
.plan__item {
   background: linear-gradient(to right bottom, #303131, #1E2023);
}

.plan__item:hover {
   cursor: pointer;
   box-shadow: 0 0 50px 0 rgba(0, 0, 0, .4);
}

.plan__item.active {
   box-shadow: 0 0 50px 0 rgba(0, 0, 0, .4),
      inset 0 0 0 1px rgba(125, 135, 151, 1);
}

.popular .card__title {
   position: relative;
}

.popular .card__title::after {
   content: "Popular";
   display: inline-block;
   padding: 8px 15px;
   border-radius: 30px;
   background: #ce1123;
   font-size: 0.75rem;
   line-height: 1;
   font-weight: 400;
   text-transform: none;
   position: absolute;
   top: 0;
   right: 0;
}

.benefits__item {
   border-top: 1px solid rgba(255, 255, 255, .1);
}

.benefits__item:last-child {
   border-bottom: 1px solid rgba(255, 255, 255, .1);
}
</style>