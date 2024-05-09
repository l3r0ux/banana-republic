<script setup lang="ts">
const emit = defineEmits(['expand-content'])

interface IProps {
  isContentExpanded: boolean
}

defineProps<IProps>()

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
        <button @click="handleClick">
          <img src="/arrow.svg" :class="isContentExpanded ? 'expanded' : 'closed'" />
        </button>
      </div>
    </div>
  </main>
</template>

<style scoped lang="scss">
.landing-section {
  position: relative;
  z-index: 3;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100vh;
  background-color: var(--br-color-yellow);
  padding: 0 3rem;

  .inner-container {
    max-height: 43.75rem;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    align-items: center;
    height: 100%;
    max-width: 17.5rem;
    margin: 0 auto;

    > img {
      object-fit: cover;
      width: 100%;
      margin-top: 1rem;
    }

    .text {
      text-align: center;
      margin-bottom: 1rem;

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
        cursor: pointer;
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
          transition: 600ms transform ease;

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

@media screen and (min-width: 960px) {
  .landing-section {
    width: fit-content;
    height: unset;
    align-items: flex-start;

    .inner-container {
      max-width: 22.5rem;
      max-height: 40.625rem;
      height: 100vh;

      > img {
        max-width: 14.75rem;
      }

      .text {
        h1 {
          margin-bottom: 1rem;
        }

        p {
          padding-bottom: 5rem;
        }

        button {
          img {
            &.closed {
              transform: rotate(0deg);
            }

            &.expanded {
              transform: rotate(180deg);
            }
          }
        }
      }
    }
  }
}

@media screen and (min-height: 740px) {
  .landing-section {
    align-items: center;
  }
}

@media screen and (max-height: 612px) and (max-width: 960px) {
  .landing-section {
    .inner-container {
      flex-direction: row;
      margin: unset;
      justify-content: center;
      gap: 2rem;
      max-width: unset;

      > img {
        margin: 0;
        max-width: 14rem;
      }

      .text {
        h1 {
          margin-bottom: 1rem;
        }

        p {
          padding-bottom: 2rem;
        }
      }
    }
  }
}
</style>
