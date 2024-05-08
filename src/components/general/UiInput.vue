<script setup lang="ts">
import { ref, onMounted } from 'vue'

interface IProps {
  type: string
  label: string
  placeholder?: string
  chips?: { name: string; iconUrl: string }[]
}

const props = defineProps<IProps>()
const emit = defineEmits(['change'])

let activeChip = ref<string>()

const handleChipClick = (chip: string) => {
  activeChip.value = chip
  emit('change', chip)
}

onMounted(() => {
  if (props.type === 'chip') activeChip.value = props.chips[0].name
})
</script>

<template>
  <div class="input-container">
    <label :for="label">{{ label }}</label>
    <input
      v-if="type !== 'chip'"
      @input="emit('change', $event.target.value)"
      :id="label"
      :type="type"
      :placeholder="placeholder"
      :name="label"
    />
    <template v-else>
      <div class="chips-container">
        <button
          @click.prevent="handleChipClick(chip.name)"
          class="chip-container"
          v-for="chip of chips"
          :key="chip"
        >
          <div class="chip" :class="activeChip === chip.name ? 'selected' : ''">
            <img :src="chip.iconUrl" />
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

  label,
  input {
    width: 100%;
  }

  label {
    padding-bottom: 0.4rem;
    font-weight: 500;
  }

  input {
    height: 3rem;
    border: 1px solid var(--br-color-cloudy-blue);
    border-radius: 4px;
    background-color: var(--br-color-pale-grey);
    padding: 0 1rem;
    font-size: 1rem;
    outline: none;
    transition: border-color 200ms ease;

    &:focus {
      border-color: var(--br-color-tangerine);
    }

    &::placeholder {
      color: var(--br-color-cloudy-blue);
      opacity: 1;
    }

    &::-ms-input-placeholder {
      color: var(--br-color-cloudy-blue);
    }
  }

  .chips-container {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1rem;
    width: 100%;
    margin-top: 0.6rem;

    .chip-container {
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
          background-color: var(--br-color-light-grey);
        }
      }

      .name {
        color: var(--br-color-cloudy-blue);
      }
    }
  }
}
</style>
