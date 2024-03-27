<template>
  <RouterView />
</template>

<script>
import { RouterView } from 'vue-router';


export default {
  name: 'HomePage',
  components: {
    RouterView
  }
}
</script>

<style lang="scss">

#app {
  font-family: 'Roboto Slab', serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: var(--c-grey-light);

  a {
    color: var(--c-purple-400);

    &:hover {
      color: var(--c-purple-500);
    }
  }
}

body {
  background: var(--c-black);
}
</style>
