<script setup lang="ts">
const emit = defineEmits(['expand-content'])

defineProps({
  isContentExpanded: String
})

const handleClick = () => {
  emit('expand-content')
}
</script>

<template>
  <main class="landing-section">
    <div class="inner-container">
      <img src="/face.svg" />
      <div class="text">
        <h1>Front-end challenge!</h1>
        <p>This is the design that you will need to code up and impress us.</p>
        <button>
          <img
            @click="handleClick"
            src="/arrow.svg"
            :class="isContentExpanded ? 'expanded' : 'closed'"
          />
        </button>
      </div>
    </div>
  </main>
</template>

<style scoped lang="scss">
.landing-section {
  display: flex;
  height: 100vh;
  background-color: var(--br-color-yellow);
  padding: 0 3rem;

  .inner-container {
    display: flex;
    flex-direction: column;
    justify-content: center;
    height: 100%;
    max-width: 280px;
    margin: 0 auto;

    > img {
      object-fit: cover;
      margin-bottom: 6rem;
      width: 100%;
    }

    .text {
      text-align: center;

      h1 {
        font-weight: bold;
        margin-bottom: 2rem;
      }

      p {
        font-weight: 500;
        font-size: 1.3rem;
        padding-bottom: 3rem;
      }

      button {
        display: flex;
        align-items: center;
        justify-content: center;
        margin: 0 auto;
        background-color: var(--br-color-charcoal-grey);
        border-radius: 100vw;
        height: 4rem;
        width: 4rem;
        border: unset;

        img {
          transition: 200ms transform ease;

          &.closed {
            transform: rotate(90deg);
          }

          &.expanded {
            transform: rotate(-90deg);
          }
        }
      }
    }
  }
}
</style>
