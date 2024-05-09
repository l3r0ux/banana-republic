<script setup lang="ts">
interface IProps {
  isContentExpanded: boolean
}

defineProps<IProps>()
</script>

<template>
  <div class="content-panel-container" :class="isContentExpanded ? 'expanded' : ''">
    <aside class="inner-container">
      <h1>My World Today</h1>
      <p>
        <span>
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Tempore, itaque illum soluta
          quasi accusamus provident cum asperiores cumque aspernatur, aliquid sit! Laborum
          reprehenderit ab doloremque.
        </span>
        <a href="#">View all days&nbsp;</a>
        <span>
          nesciunt voluptate quam autem quas in deserunt, eligendi, voluptatem, ad corporis possimus
          non consectetur qui delectus laudantium cum. Libero dolorum maiores excepturi dignissimos
          et non quisquam, quod labore perferendis ipsam quia quam similique architecto. Inventore
          blanditiis optio aperiam dolor, animi accusantium natus, consequatur dolorem
          exercitationem, commodi incidunt molestiae ullam provident facere nesciunt. Ratione
          debitis quisquam aliquam, ullam voluptatibus praesentium aspernatur nam dolorem adipisci.
          Ullam eveniet officiis consectetur et cum enim voluptate dolor ex.
        </span>
      </p>
    </aside>
  </div>
</template>

<style scoped lang="scss">
.content-panel-container {
  position: absolute;
  top: -100%;
  left: 0;
  z-index: 2;
  height: 100%;
  width: 100%;
  background-color: var(--br-color-tangerine);
  transition: top 600ms ease;

  &.expanded {
    top: 0;
  }

  .inner-container {
    overflow: scroll;
    line-height: 1.6;
    height: 100%;
    width: 100%;
    padding: 3rem 2rem;
    max-width: 22.5rem;
    margin: 0 auto;

    h1 {
      font-weight: bold;
      margin-bottom: 2rem;
      font-size: 2rem;
    }

    p {
      font-weight: 500;
      font-size: 1rem;
    }
  }
}

@media screen and (min-width: 60rem) {
  .content-panel-container {
    top: 0;
    left: -100%;
    transition: left 600ms ease;

    &.expanded {
      left: 0;
    }

    .inner-container {
      display: flex;
      flex-direction: column;
      justify-content: center;
      max-width: 40.625rem;
      max-height: 40.625rem;
      height: 100vh;
    }
  }
}
</style>
