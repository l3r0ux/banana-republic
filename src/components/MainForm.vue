<script setup lang="ts">
import UiInput from '../components/general/UiInput.vue'
import ContentPanel from './ContentPanel.vue'

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

const handleSubmit = () => {
  console.log(formValue)
}

const clearForm = () => {
  formValue.name = null
  formValue.gender = 'Male'
  formValue.dateOfBirth = null
  formValue.email = null
  formValue.mobile = null
  formValue.customerId = null
  formValue.membership = 'Classic'

  const form: HTMLFormElement | null = document.querySelector('.form')
  form?.reset()
}
</script>

<template>
  <section class="form-section">
    <form @submit.prevent="handleSubmit" class="form">
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
          { name: 'Male', iconUrl: '/mars-symbol' },
          { name: 'Female', iconUrl: '/venus-symbol' }
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
        type="tel"
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
          { name: 'Classic', iconUrl: '/card' },
          { name: 'Silver', iconUrl: '/card' },
          { name: 'Gold', iconUrl: '/card' }
        ]"
      />
      <button @click.prevent="clearForm" class="button cancel">CANCEL</button>
      <button type="submit" class="button save">SAVE</button>
    </form>
    <ContentPanel :isContentExpanded="isContentExpanded" />
  </section>
</template>

<style scoped lang="scss">
.form-section {
  position: relative;
  z-index: 1;
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
    margin-bottom: 1rem;

    .button {
      width: 100%;
      border: unset;
      background-color: unset;
      font-size: 1.1rem;
      border-radius: 0.4rem;
      padding: 1rem 0;
      cursor: pointer;

      &.cancel {
        margin-bottom: 0.5rem;
        background-color: var(--br-color-pale-grey);
      }

      &.save {
        background-color: var(--br-color-blue-green);
        color: white;
      }
    }
  }
}
</style>
