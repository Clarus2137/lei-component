<script setup>

</script>



<template>
   <div class="confirm__chosen chosen active max-w-[800px] mx-auto mt-[100px] p-[60px] rounded-[1.125rem]">
      <div class="chosen__title">
         <p class="tagline text-light font-extralight text-[1.125rem] leading-[1.2]">Selected plan:</p>
         <p class="headline mt-[15px] font-axiforma font-semibold text-[45px]">Starter</p>
      </div>
      <div class="chosen__body flex jystify-between w-full mt-10">
         <div class="chosen__info w-[48%]">
            <div class="chosen__years text-light font-extralight text-[1.125rem] leading-[1.2]">Duration: <span
                  class="text-[1.25rem] leading-[1] font-medium">1 year</span></div>
            <div class="chosen__price mt-2.5 text-light font-extralight text-[1.125rem] leading-[1.2]">Cost: <span
                  class="text-[1.25rem] leading-[1] font-medium">70&#163;</span></div>
         </div>
         <div class="chosen__benefits benefits w-[48%]">
            <p class="benefits__title mb-[15px] text-[1.125rem] leading-[1.2] font-extralight">Selected plan includes:</p>
            <div class="benefits__item py-[15px] text-[1.125rem] leading-[1.2] font-extralight">
               <p class="flex gap-x-[15px]">
                  <svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
                     <path
                        d="M9.99999 18.3333C14.6024 18.3333 18.3333 14.6023 18.3333 9.99996C18.3333 5.39759 14.6024 1.66663 9.99999 1.66663C5.39762 1.66663 1.66666 5.39759 1.66666 9.99996C1.66666 14.6023 5.39762 18.3333 9.99999 18.3333Z"
                        fill="#FAFAFA" />
                     <path d="M7.5 10L9.16667 11.6667L12.5 8.33337" stroke="black" stroke-width="1.5"
                        stroke-linecap="round" stroke-linejoin="round" />
                  </svg>
                  <span>Plan Benefits / Plan Benefits</span>
               </p>
            </div>
            <div class="benefits__item py-[15px] text-[1.125rem] leading-[1.2] font-extralight">
               <p class="flex gap-x-[15px]">
                  <svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
                     <path
                        d="M9.99999 18.3333C14.6024 18.3333 18.3333 14.6023 18.3333 9.99996C18.3333 5.39759 14.6024 1.66663 9.99999 1.66663C5.39762 1.66663 1.66666 5.39759 1.66666 9.99996C1.66666 14.6023 5.39762 18.3333 9.99999 18.3333Z"
                        fill="#FAFAFA" />
                     <path d="M7.5 10L9.16667 11.6667L12.5 8.33337" stroke="black" stroke-width="1.5"
                        stroke-linecap="round" stroke-linejoin="round" />
                  </svg>
                  <span>Plan Benefits / Plan Benefits</span>
               </p>
            </div>
            <div class="benefits__item py-[15px] text-[1.125rem] leading-[1.2] font-extralight">
               <p class="flex gap-x-[15px]">
                  <svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
                     <path
                        d="M9.99999 18.3333C14.6024 18.3333 18.3333 14.6023 18.3333 9.99996C18.3333 5.39759 14.6024 1.66663 9.99999 1.66663C5.39762 1.66663 1.66666 5.39759 1.66666 9.99996C1.66666 14.6023 5.39762 18.3333 9.99999 18.3333Z"
                        fill="#FAFAFA" />
                     <path d="M7.5 10L9.16667 11.6667L12.5 8.33337" stroke="black" stroke-width="1.5"
                        stroke-linecap="round" stroke-linejoin="round" />
                  </svg>
                  <span>Plan Benefits / Plan Benefits</span>
               </p>
            </div>
         </div>
      </div>
   </div>
   <div class="checkbox-wrapper mt-10 inline-block relative">
      <label class="text-light text-[1.125rem] leading-[1.2] font-extralight">
         <input type="checkbox" class="mr-[15px]">
         <div class="custom-checkbox"></div>
         I confirm that i have read the <span class="font-medium">Terms & Conditions</span> and <span
            class="font-medium">Privacy Policy</span>
      </label>
   </div>
   <div class="text-center mt-[50px]">
      <button type="button" class="confirm__btn py-[15px] px-[30px] bg-primary border border-solid border-primary rounded-[30px] text-light text-[1.125rem] leading-[1] font-medium duration-300 hover:bg-transparent hover:border-white hover:text-white">Confirm and continue</button>
   </div>
</template>



<style scoped>
.chosen {
   background: linear-gradient(to right bottom, #303131, #1E2023);
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

.custom-checkbox {
   width: 17px;
   height: 16px;
   background: url("../assets/img/unchecked.png") no-repeat center;
   background-size: contain;
   position: absolute;
   left: 0;
   top: 50%;
   transform: translateY(-50%);
}

[type="checkbox"] {
   opacity: 0;
   margin-right: 15px;
}

[type="checkbox"]:checked+.custom-checkbox {
   width: 16px;
   height: 16px;
   background: url("../assets/img/checked.png") no-repeat center;
}

.checkbox-wrapper>label:hover {
   cursor: pointer;
}
</style>