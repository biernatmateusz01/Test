<template>
  <aside>
    <button @click="toogleMenu" class="hamburger">
      <svg
        v-if="!openMenu"
        xmlns="http://www.w3.org/2000/svg"
        fill="none"
        viewBox="0 0 24 24"
        stroke-width="1.5"
        stroke="currentColor"
        class="w-6 h-6"
      >
        <path
          stroke-linecap="round"
          stroke-linejoin="round"
          d="M3.75 6.75h16.5M3.75 12h16.5m-16.5 5.25h16.5"
        />
      </svg>
      <svg
        v-else
        xmlns="http://www.w3.org/2000/svg"
        fill="none"
        viewBox="0 0 24 24"
        stroke-width="1.5"
        stroke="currentColor"
        class="w-6 h-6"
      >
        <path stroke-linecap="round" stroke-linejoin="round" d="M6 18L18 6M6 6l12 12" />
      </svg>
    </button>

    <nav v-if="openMenu" class="mobile">
      <ul class="nav column">
        <li class="nav__item"><a href="#">Dashboard</a></li>
        <li class="nav__item"><a href="#">Reports</a></li>
        <li class="nav__item"><a href="#">Expenses</a></li>
        <li class="nav__item"><a href="#">Settings</a></li>
        <li class="nav__item"><a href="#">Profile</a></li>
        <li class="nav__item"><a href="#">Log out</a></li>
      </ul>
    </nav>
    <nav class="desktop">
      <ul class="nav">
        <li class="nav__item"><a href="#">Dashboard</a></li>
        <li class="nav__item"><a href="#">Reports</a></li>
        <li class="nav__item"><a href="#">Expenses</a></li>
        <li class="nav__item"><a href="#">Settings</a></li>
        <li class="nav__item"><a href="#">Profile</a></li>
        <li class="nav__item"><a href="#">Log out</a></li>
      </ul>
    </nav>
  </aside>
</template>

<script setup>
import { ref } from 'vue'
const openMenu = ref(false)

const toogleMenu = () => {
  openMenu.value = !openMenu.value
}
</script>

<style scoped>
li {
  list-style: none;
}
.nav {
  display: flex;
  justify-content: end;
  gap: 40px;
  font-size: 17px;
  text-transform: uppercase;
  margin-bottom: 20px;
  text-decoration: none;
}
.mobile {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  background: white;
  height: 100vh;
  width: 100vw;
  position: fixed;
  top: 0;
  left: 0;
}
.desktop {
  display: none;
}
.column {
  flex-direction: column;
}
.hamburger {
  height: 24px;
  width: 24px;
  background: #00dcc2;
  border-radius: 100%;
  position: fixed;
  top: 12px;
  right: 12px;
  z-index: 50;
  border: none;
  padding: 2px;
}
.nav__item {
  text-decoration: none;
  font-weight: 600;
  color: #00dcc2;
}
li > a {
  text-decoration: none;
  color: #00dcc2;
}
@media (min-width: 768px) {
  .mobile {
    display: none;
  }
  .desktop {
    display: flex;
    justify-content: end;
  }
  .hamburger {
    display: none;
  }
}
</style>
