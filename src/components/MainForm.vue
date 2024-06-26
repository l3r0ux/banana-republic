<script setup lang="ts">
import { reactive } from 'vue'
import UiInput from '../components/general/UiInput.vue'
import ContentPanel from './ContentPanel.vue'

interface IProps {
  isContentExpanded: boolean
}

defineProps<IProps>()

let formValue = reactive({
  name: '',
  gender: 'Male',
  dateOfBirth: '',
  email: '',
  mobile: '',
  customerId: '',
  membership: 'Classic'
})

const clearForm = () => {
  formValue.name = ''
  formValue.gender = 'Male'
  formValue.dateOfBirth = ''
  formValue.email = ''
  formValue.mobile = ''
  formValue.customerId = ''
  formValue.membership = 'Classic'
}

const handleSubmit = () => {
  console.log(formValue)
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
        :input-value="formValue.name"
      />
      <UiInput
        @change="formValue.gender = $event"
        label="Gender"
        type="chip"
        :chips="[
          { name: 'Male', iconUrl: '/mars-symbol' },
          { name: 'Female', iconUrl: '/venus-symbol' }
        ]"
        :input-value="formValue.gender"
      />
      <UiInput
        @change="formValue.dateOfBirth = $event"
        label="Date of Birth"
        type="date"
        :input-value="formValue.dateOfBirth"
      />
      <UiInput
        @change="formValue.email = $event"
        label="Email"
        type="email"
        placeholder="kendall@email.com"
        :input-value="formValue.email"
      />
      <UiInput
        @change="formValue.mobile = $event"
        label="Mobile"
        type="tel"
        placeholder="+91 98765 43210"
        :input-value="formValue.mobile"
      />
      <UiInput
        @change="formValue.customerId = $event"
        label="Customer ID"
        type="text"
        placeholder="576802-ERD0348 45"
        :input-value="formValue.customerId"
      />
      <UiInput
        class="membership-input"
        @change="formValue.membership = $event"
        label="Membership"
        type="chip"
        :chips="[
          { name: 'Classic', iconUrl: '/card' },
          { name: 'Silver', iconUrl: '/card' },
          { name: 'Gold', iconUrl: '/card' }
        ]"
        :input-value="formValue.membership"
      />
      <div class="form-controls">
        <button @click.prevent="clearForm" class="button cancel">CANCEL</button>
        <button type="submit" class="button save">SAVE</button>
      </div>
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
  width: 100%;
  min-height: 100vh;

  .form {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    padding: 0 1rem 1rem 1rem;
    max-width: 22.5rem;
    margin: 0 auto;

    .form-controls {
      width: 100%;

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
}

@media screen and (min-width: 60rem) {
  .form-section {
    padding-top: 6rem;

    .form {
      max-width: 41.5rem;
      width: 100%;
      padding: 0 4rem;
      .membership-input {
        margin-top: 2rem;
      }

      .form-controls {
        width: 100%;
        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: flex-end;
        gap: 1rem;
        margin-top: 3rem;
        margin-bottom: 1rem;

        .button {
          width: unset;
          padding: 1rem;
          min-width: 9.25rem;
          font-size: 1rem;
          font-weight: 500;

          &.cancel {
            margin-bottom: unset;
          }
        }
      }
    }
  }
}
</style>
