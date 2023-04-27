<script setup>
import { RouterView, RouterLink } from 'vue-router'
</script>

<template>
  <header class="container">
    <RouterLink to="/">Home</RouterLink>
    <RouterLink to="/about">About</RouterLink>
  </header>
  <Transition name="route">
    <RouterView />
  </Transition>
</template>

<style scoped lang="scss">
$header-line-height: 1.5;
$header-max-height: 100vh;
$nav-font-size: 12px;
$nav-border-color: var(--color-border);
$nav-active-color: var(--color-text);

header {
  line-height: $header-line-height;
  max-height: $header-max-height;

  // .logo {
  //   display: block;
  //   margin: 0 auto 2rem;
  // }

  // nav {
  //   width: 100%;
  //   font-size: $nav-font-size;
  //   text-align: center;
  //   margin-top: 2rem;

  //   a.router-link-exact-active {
  //     color: $nav-active-color;

  //     &:hover {
  //       background-color: transparent;
  //     }
  //   }

  //   a {
  //     display: inline-block;
  //     padding: 0 1rem;
  //     border-left: 1px solid $nav-border-color;

  //     &:first-of-type {
  //       border: 0;
  //     }
  //   }
  // }

  @media (min-width: 1024px) {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);

    // .logo {
    //   margin: 0 2rem 0 0;
    // }

    // .wrapper {
    //   display: flex;
    //   place-items: flex-start;
    //   flex-wrap: wrap;
    // }

    // nav {
    //   text-align: left;
    //   margin-left: -1rem;
    //   font-size: 1rem;
    //   padding: 1rem 0;
    //   margin-top: 1rem;
    // }
  }
}

.container {
  max-width: 300px;
  margin: 10px auto;

  a {
    margin-right: 1rem;
    margin-bottom: 1rem;
  }
}

// Route Animation
.route-enter-from {
  opacity: 0;
  transform: translateX(100px);
}

.route-enter-to {
  opacity: 1;
  transform: translateX(0);
}

.route-enter-active {
  transition: all 0.5s ease;
}
</style>
