<script setup>
import { RouterLink } from "vue-router";
</script>

<template>
  <header>
    <nav class="container">
      <div class="branding">
        <img class="logo" src="../assets/Vue_Logo_Black.png" alt="Vue Logo" />
        <span>/</span>
        <img class="profile" src="../assets/profile.jpg" alt="" />
        <h1>Vue Todo Prototype</h1>
        <p>Test</p>
        <svg
          xmlns="http://www.w3.org/2000/svg"
          fill="none"
          viewBox="0 0 24 24"
          stroke-width="1.5"
          stroke="currentColor"
          class="size-6"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            d="M10.5 6h9.75M10.5 6a1.5 1.5 0 1 1-3 0m3 0a1.5 1.5 0 1 0-3 0M3.75 6H7.5m3 12h9.75m-9.75 0a1.5 1.5 0 0 1-3 0m3 0a1.5 1.5 0 0 0-3 0m-3.75 0H7.5m9-6h3.75m-3.75 0a1.5 1.5 0 0 1-3 0m3 0a1.5 1.5 0 0 0-3 0m-9.75 0h9.75"
          />
        </svg>
        <p
          class="hide--text"
          style="background-color: transparent; padding: 0; margin: 5px"
        >
          in process...
        </p>
      </div>
      <ul class="nav-routes">
        <div class="routes--wrapper">
          <p class="special__route">Feedback</p>
          <RouterLink to="/">Home</RouterLink>
          <!-- In order for users to switch pages inside the Vue Application we need to use a component called routerLink -->
          <RouterLink to="/about">About</RouterLink>
          <!-- Inside the router folder in the index.js file we can see all the routes inside this application -->
          <p>Help</p>
          <p>Docs</p>
        </div>
        <div class="profile--notification">
          <div class="notification">
            <div class="note-ball"></div>
            <svg
              xmlns="http://www.w3.org/2000/svg"
              fill="#000"
              viewBox="0 0 24 24"
              stroke-width="1.5"
              stroke="#000"
              class="size-6"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                d="M14.857 17.082a23.848 23.848 0 0 0 5.454-1.31A8.967 8.967 0 0 1 18 9.75V9A6 6 0 0 0 6 9v.75a8.967 8.967 0 0 1-2.312 6.022c1.733.64 3.56 1.085 5.455 1.31m5.714 0a24.255 24.255 0 0 1-5.714 0m5.714 0a3 3 0 1 1-5.714 0"
              />
            </svg>
            <img
              class="profile"
              style="width: 30px"
              src="../assets/profile.jpg"
              alt=""
            />
          </div>
        </div>
      </ul>
    </nav>
  </header>
</template>

<style lang="scss" scoped>
/* The "scoped" attribute is going to scope all the styles that are defined within this component to only this component(if we have another header tag...
styling in another component, it wouldn't mattered, because this one is scoped, it only be applied to this component) */

header {
  background-color: #0a0a0a;
  border-bottom: solid 1px rgba(255, 255, 255, 0.103);
  nav {
    display: flex;
    align-items: center;
    padding: 25px 16px;

    .branding {
      display: flex;
      align-items: center;
      position: relative;
      gap: 8px;
      img {
        max-width: 50px;
      }

      span {
        color: #303030;
        font-size: 24px;
        font-weight: 400;
        font-style: italic;
        position: absolute;
        left: 12%;
        top: 12%;
      }

      h1 {
        font-size: 12px;
        font-family: "inter";
        font-weight: 500;
      }
      p {
        background-color: #1f1f1f;
        font-size: 12px;
        font-weight: 500;
        padding: 3px 12px;
        border-radius: 25px;
        margin-left: 10px;
      }
      svg {
        width: 22px;
        border-radius: 5px;
        color: #a1a1a1;
        cursor: not-allowed;
        transition: all 300ms ease;
        padding: 6px 2px;

        &:hover {
          background-color: #1f1f1f;
          padding: 6px 2px;
        }
        &:hover ~ .hide--text {
          opacity: 1;
        }
      }
    }

    .routes--wrapper {
      display: flex;
      justify-content: center;
      align-items: center;
      gap: 15px;
    }

    .nav-routes {
      display: flex;
      flex: 1;
      justify-content: center;
      align-self: center;
      justify-content: flex-end;
      color: #a1a1a1;
      font-weight: 800;
      list-style: none;
      font-size: 12px;
      p {
        color: #a1a1a1;
        font-family: "inter" !important;
        font-weight: 400;
        cursor: pointer;
        transition: all 200ms ease;
        &:hover {
          color: #ededed;
        }
      }
      a {
        text-decoration: none;
        color: #a1a1a1;
        font-weight: 400;
        font-family: "inter" !important;
        transition: all 200ms ease;
        &:hover {
          color: #ededed;
        }
      }
    }
  }

  .profile--notification {
    margin-left: 30px;
    .notification {
      display: flex;
      align-items: center;
      justify-content: center;
      svg {
        fill: white;
        width: 30px;
        border: 1.5px solid hsla(0, 0%, 100%, 0.14);
        border-radius: 50%;
        padding: 5px;
        transition: all 300ms ease;
        cursor:pointer;

        &:hover {
          opacity: 0.8;
        }
      }

      img {
        cursor: pointer
      }

      .note-ball {
        background-color: rgb(47, 146, 192);
        width: 10px;
        height: 10px;
        border-radius: 20px;
        display: none;
      }
    }
  }

  .special__route {
    border: 1px solid hsla(0, 0%, 100%, 0.14);
    padding: 8px 10px;
    border-radius: 6px;
    cursor: pointer;
    transition: color 300ms ease;
    transition: background-color 500ms ease;
  }

  .hide--text {
    opacity: 0;
    transition: all 300ms ease;
  }

  .special__route:hover {
    background-color: #181717;
    color: #ededed;
  }
  .profile {
    width: 20px;
    border-radius: 50px;
    margin-left: 10px;
    border: 1px solid gray;
  }

  .logo {
    margin-right: 10px;
  }
}
</style>
