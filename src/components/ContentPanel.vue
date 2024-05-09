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
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Tempore, itaque illum soluta quasi
        accusamus provident cum asperiores cumque aspernatur, aliquid sit! Laborum reprehenderit ab
        doloremque facere aspernatur nesciunt voluptate quam autem quas in deserunt, eligendi,
        voluptatem, ad corporis possimus non consectetur qui delectus laudantium cum. Libero dolorum
        maiores excepturi dignissimos et non quisquam, quod labore perferendis ipsam quia quam
        similique architecto. Inventore blanditiis optio aperiam dolor, animi accusantium natus,
        consequatur dolorem exercitationem, commodi incidunt molestiae ullam provident facere
        nesciunt. Ratione debitis quisquam aliquam, ullam voluptatibus praesentium aspernatur nam
        dolorem adipisci. Ullam eveniet officiis consectetur et cum enim voluptate dolor ex.
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
    line-height: 1.6;
    height: 100%;
    width: 100%;
    padding: 3rem 2rem;
    max-width: 360px;
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
</style>
