<template>
  <footer>
    <div class="logoWrapper">
      <img
        alt="Vue logo"
        class="logo"
        src="@/assets/logo.svg"
        width="75"
        height="75"
      />
    </div>

    <div class="wrapper">
      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
      </nav>
    </div>
  </footer>
</template>

<script>
import { RouterLink, RouterView } from "vue-router";

export default {
  name: "Footer",
  props: {
    title: {
      type: String,
      default: "Link",
    },
  },
  components: {
    RouterLink,
  },
};
</script>

<style scoped>
footer {
  line-height: 1.5;
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  align-content: center;
}

.logo {
  margin-top: 25px;
  margin-bottom: 25px;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    justify-content: space-between;
    padding: 0px 50px;
  }

  .logo {
  }
  .logoWrapper {
  }

  .wrapper {
    display: flex;
    justify-content: flex-start;
  }
  header .wrapper {
    display: flex;
    flex-direction: row;
  }

  nav {
    text-align: left;
    margin-left: 1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}
</style>

