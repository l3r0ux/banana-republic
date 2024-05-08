<script setup lang="ts">
import UiInput from '../components/general/UiInput.vue'

interface IProps {
  isContentExpanded: boolean
}

defineProps<IProps>()

const formValue = {
  name: null,
  gender: 'Male',
  dateOfBirth: null,
  email: null,
  mobile: null,
  customerId: null,
  membership: 'Classic'
}

const handleSubmit = (_event: Event) => {
  console.log(formValue)
}
</script>

<template>
  <section class="form-section">
    <form @submit.prevent="handleSubmit($event)" class="form">
      <UiInput
        @change="formValue.name = $event"
        label="Name"
        type="text"
        placeholder="Kendal Jenner"
      />
      <UiInput
        @change="formValue.gender = $event"
        label="Gender"
        type="chip"
        :chips="[
          { name: 'Male', iconUrl: '/mars-symbol.svg' },
          { name: 'Female', iconUrl: '/venus-symbol.svg' }
        ]"
      />
      <UiInput @change="formValue.dateOfBirth = $event" label="Date of Birth" type="date" />
      <UiInput
        @change="formValue.email = $event"
        label="Email"
        type="email"
        placeholder="kendall@email.com"
      />
      <UiInput
        @change="formValue.mobile = $event"
        label="Mobile"
        type="number"
        placeholder="+91 98765 43210"
      />
      <UiInput
        @change="formValue.customerId = $event"
        label="Customer ID"
        type="text"
        placeholder="576802-ERD0348 45"
      />
      <UiInput
        @change="formValue.membership = $event"
        label="Membership"
        type="chip"
        :chips="[
          { name: 'Classic', iconUrl: '/card.svg' },
          { name: 'Silver', iconUrl: '/card.svg' },
          { name: 'Gold', iconUrl: '/card.svg' }
        ]"
      />
    </form>
  </section>
</template>

<style scoped lang="scss">
.form-section {
  display: flex;
  flex-direction: column;
  background-color: #fff;
  padding-top: 3rem;
  max-width: 360px;
  margin: 0 auto;

  .form {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    padding: 0 1rem;
  }
}
</style>
