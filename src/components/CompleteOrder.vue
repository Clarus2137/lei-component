<script setup>
import { ref, computed } from 'vue';


const props = defineProps({
   currentSubscriptionType: String
});

const currentSubscriptionType = computed(() => props.currentSubscriptionType || '');

const form = ref({
   legalEntityName: '',
   companyNumber: '',
   firstName: '',
   secondName: '',
   email: '',
   vatNumber: '',
   phoneNumber: '',
   selectedCountry: '',
   registrationAuthority: '',
   legalForm: '',
   foundationDate: '',
   entityAddress: {
      street: '',
      city: '',
      postalCode: '',
      country: '',
      region: '',
   },
   headquartersAddressIsIdentical: true,
   isOwnedByAnotherCompany: false,
   headquartersAddress: {
      street: '',
      city: '',
      postalCode: '',
      country: '',
      region: '',
   },
   lei: ''
});

function submitForm() {
   console.log(form.value);
   // Send form
}

// Reset by changing country
function onCountryChange() {
   form.value.registrationAuthority = '';
   form.value.legalForm = '';
   form.value.entityAddress.region = '';
}
</script>



<template>
   <p class="headline font-axiforma font-semibold text-[45px] text-center">Complete your order</p>
   <p class="tagline text-xl text-center text-dark">Fill out the fields below to complete your order</p>
   <form @submit.prevent="submitForm" v-if="currentSubscriptionType === 'Registration'">
      <p class="basic-title flex gap-x-10 w-full my-[60px] text-[1.875rem] leading-[1.4] font-semibold">Basic information</p>
      <div class="grid grid-cols-2 gap-x-[60px] gap-y-[25px]">
         <div>
            <input placeholder="Legal entity name" v-model="form.legalEntityName" type="text" required>
         </div>
         <div>
            <input placeholder="Company number / Registration ID" v-model="form.companyNumber" type="text" required>
         </div>
         <div>
            <input placeholder="Applicant first name" v-model="form.firstName" type="text" required>
         </div>
         <div>
            <input placeholder="Applicant second name" v-model="form.secondName" type="text" required>
         </div>
         <div>
            <input placeholder="Email" v-model="form.email" type="email" required>
         </div>
         <div>
            <input placeholder="VAT number (if applicable)" v-model="form.vatNumber" type="text">
         </div>
         <div>
            <input placeholder="Phone number" v-model="form.phoneNumber" type="tel" required>
         </div>
         <div class="select-wrapper">
            <select v-model="form.selectedCountry" @change="onCountryChange" required>
               <option disabled value="">Select country</option>
               <!-- Country options -->
            </select>
         </div>
         <div class="select-wrapper">
            <select v-model="form.registrationAuthority" :disabled="!form.selectedCountry" required>
               <option disabled value="">Registration authority</option>
               <!-- Authority options -->
            </select>
         </div>
         <div class="select-wrapper">
            <select v-model="form.legalForm" :disabled="!form.registrationAuthority" required>
               <option disabled value="">Legal form of the company</option>
               <!-- Options for company forms -->
            </select>
         </div>
         <div>
            <input placeholder="Foundation date" v-model="form.foundationDate" type="date" required>
         </div>
      </div>
      <p class="entity-title flex gap-x-10 w-full my-[60px] text-[1.875rem] leading-[1.4] font-semibold">Entity address</p>
      <div class="grid grid-cols-2 gap-x-[60px] gap-y-[25px]">
         <div>
            <input placeholder="Street" v-model="form.entityAddress.street" type="text" required>
         </div>
         <div>
            <input placeholder="City" v-model="form.entityAddress.city" type="text" required>
         </div>
         <div>
            <input placeholder="Postal Code" v-model="form.entityAddress.postalCode" type="text" required>
         </div>
         <div class="select-wrapper">
            <select v-model="form.entityAddress.country" @change="onCountryChange" required>
               <option disabled value="">Select country</option>
               <!-- Options for countries -->
            </select>
         </div>
         <div class="select-wrapper">
            <select v-model="form.entityAddress.region" :disabled="!form.entityAddress.country" required>
               <option disabled value="">Select region</option>
               <!-- Options for regions -->
            </select>
         </div>
      </div>

      <div class="confirmation-wrapper">
         <div class="checkbox-wrapper">
            <label>
               <input type="checkbox" v-model="form.headquartersAddressIsIdentical">
               <div class="custom-checkbox"></div>
               Headquarters address is identical to legal address?
            </label>
         </div>
         <div class="checkbox-wrapper">
            <label>
               <input type="checkbox" v-model="form.isOwnedByAnotherCompany">
               <div class="custom-checkbox"></div>
               Is the company owned by another company?
            </label>
         </div>
      </div>

      <!-- Show/Hide headquarters address -->
      <div v-if="!form.headquartersAddressIsIdentical">
         <p class="headquarter-title  flex gap-x-10 w-full my-[60px] text-[1.875rem] leading-[1.4] font-semibold">Headquarters address</p>
         <div>
            <input placeholder="Street" v-model="form.headquartersAddress.street" type="text" required>
         </div>
         <div>
            <input placeholder="City" v-model="form.headquartersAddress.city" type="text" required>
         </div>
         <div>
            <input placeholder="Postal Code" v-model="form.headquartersAddress.postalCode" type="text" required>
         </div>
         <div class="select-wrapper">
            <select v-model="form.headquartersAddress.country" required>
               <option disabled value="">Select country</option>
               <!-- Options for countries -->
            </select>
         </div>
         <div class="select-wrapper">
            <select v-model="form.headquartersAddress.region" :disabled="!form.headquartersAddress.country" required>
               <option disabled value="">Select region</option>
               <!-- Options for regions -->
            </select>
         </div>
         <button type="submit">Submit</button>
      </div>
   </form>
   <div v-else>
      <input placeholder="LEI or company number" v-model="form.lei" type="text" required>
   </div>
</template>



<style scoped>
form [class*="-title"]::after {
   content: "";
   align-self: flex-end;
   flex-grow: 1;
   height: 1px;
   background: #e4e4e4;
}

form [class*="-title"]:first-child {
   margin-top: 120px;
}

input:not([type="checkbox"]),
.select-wrapper {
   width: 100%;
   height: 60px;
   padding: 19px 30px;
   border: 1px solid #e4e4e4;
}

.select-wrapper>select {
   width: 100%;
   height: 100%;
   outline: none;
}

.confirmation-wrapper {
   display: flex;
   flex-wrap: wrap;
   row-gap: 25px;
   margin: 60px 0;
}

.checkbox-wrapper {
   width: 100%;
   position: relative;
}

.checkbox-wrapper>label:hover {
   cursor: pointer;
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
</style>