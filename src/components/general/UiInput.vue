<script setup lang="ts">
interface IProps {
  type: string
  label: string
  inputValue: string
  placeholder?: string
  chips?: { name: string; iconUrl: string }[]
}

defineProps<IProps>()
const emit = defineEmits(['change'])

const handleChipClick = (chip: string) => {
  emit('change', chip)
}

const handleInput = (event: Event) => {
  emit('change', (event.target as HTMLInputElement).value)
}
</script>

<template>
  <div class="input-container">
    <label :for="label">{{ label }}</label>
    <div class="input-wrapper" v-if="type !== 'chip'">
      <img v-if="type === 'date'" src="/calendar.svg" />
      <input
        @input="handleInput"
        :id="label"
        :type="type"
        :placeholder="placeholder"
        :name="label"
        :value="inputValue"
      />
    </div>
    <template v-else>
      <div class="chips-container">
        <button
          @click.prevent="handleChipClick(chip.name)"
          class="chip-container"
          v-for="chip of chips"
          :key="chip.name"
        >
          <div class="chip" :class="inputValue === chip.name ? 'selected' : ''">
            <img
              :src="inputValue === chip.name ? `${chip.iconUrl}--white.svg` : `${chip.iconUrl}.svg`"
            />
          </div>
          <span class="name">{{ chip.name }}</span>
        </button>
      </div>
    </template>
  </div>
</template>

<style scoped lang="scss">
.input-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  width: 100%;
  text-align: left;
  margin-bottom: 1rem;

  label {
    padding-bottom: 0.4rem;
    font-weight: 500;
    width: 100%;
  }

  .input-wrapper {
    position: relative;
    width: 100%;

    input {
      width: 100%;
      height: 3rem;
      border: 1px solid var(--br-color-pale-grey);
      border-radius: 0.0625rem;
      background-color: var(--br-color-pale-grey);
      padding: 0 1rem;
      font-size: 1rem;
      outline: none;
      transition:
        border-color 200ms ease,
        background-color 200ms ease;

      &:focus {
        border-color: var(--br-color-cloudy-blue);
        background-color: #fff;
      }

      &::placeholder {
        color: var(--br-color-cloudy-blue);
        opacity: 1;
      }

      &::-ms-input-placeholder {
        color: var(--br-color-cloudy-blue);
      }
    }

    @supports selector(::-webkit-calendar-picker-indicator) {
      input[type='date']::-webkit-calendar-picker-indicator {
        position: absolute;
        top: 0;
        right: 0;
        opacity: 0;
        z-index: 2;
        width: 15%;
        height: 100%;

        &:hover {
          cursor: pointer;
        }
      }

      img {
        position: absolute;
        right: 1.125rem;
        top: 0.9rem;
        pointer-events: none;
        background-color: var(--br-color-pale-grey);
      }
    }

    @supports not selector(::-webkit-calendar-picker-indicator) {
      img {
        display: none;
      }
    }
  }

  .chips-container {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1rem;
    width: 100%;
    margin-top: 0.6rem;

    .chip-container {
      cursor: pointer;
      display: flex;
      align-items: center;
      border: unset;
      background-color: unset;

      .chip {
        display: flex;
        align-items: center;
        justify-content: center;
        border-radius: 100vw;
        height: 3rem;
        width: 3rem;
        background-color: var(--br-color-pale-grey);
        margin-right: 1.2rem;
        transition: background-color 200ms ease;

        &.selected {
          background-color: var(--br-color-cloudy-darker-blue);
        }
      }

      .name {
        color: var(--br-color-cloudy-darker-blue);
      }
    }
  }
}

@media screen and (min-width: 60rem) {
  .input-container {
    flex-direction: row;
    align-items: center;
    justify-content: start;
    margin-bottom: 1.5rem;

    label {
      flex: 2;
    }

    .input-wrapper,
    .chips-container {
      flex: 5;
    }

    .chips-container {
      grid-template-columns: repeat(3, auto);
      margin-top: 0;
    }
  }
}
</style>
