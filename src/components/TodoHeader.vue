<script setup>

import { RouterLink } from 'vue-router';

</script>

<template>
  <header>
    <nav class="container">
        <div class="branding">
            <img src="../assets/Vue_Logo_Black.png" alt="Vue Logo">
            <h1>Vue Todos</h1>
        </div>
        <ul class="nav-routes">
            <RouterLink to="/">Home</RouterLink> <!-- In order for users to switch pages inside the Vue Application we need to use a component called routerLink -->
            <RouterLink to="/about">About</RouterLink> <!-- Inside the router folder in the index.js file we can see all the routes inside this application -->
        </ul>
    </nav>
  </header>
</template>

<style lang="scss" scoped> /* The "scoped" attribute is going to scope all the styles that are defined within this component to only this component(if we have another header tag...
styling in another component, it wouldn't mattered, because this one is scoped, it only be applied to this component) */

header {
  background-color: #f1f1f1;
  nav {
    display: flex;
    align-items: center;
    padding: 25px 16px;

    .branding {
      display: flex;
      align-items: center;
      gap: 8px;
      img {
        max-width: 50px;
      }

      h1 {
        font-size: 24px;
        font-weight: 800;
      }
    }

    .nav-routes {
      display: flex;
      flex: 1;
      justify-content: flex-end;
      gap: 12px;
      list-style: none;

      a {
        text-decoration: none;
        color: inherit;
      }
    }
  }
}

</style>
