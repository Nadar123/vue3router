<template>
  <nav id="nav">
    <p class="logo">Hoilday App</p>
    <ul class="nav-links">
      <li class="links">
        <router-link to="/">Home</router-link>
      </li>
      <li
        v-for="destination in destinations"
        :key="destination.name"
        class="links"
      >
        <router-link
          :to="{
            name: 'DestinationDetails',
            params: { slug: destination.slug }
          }"
        >
          {{ destination.name }}
        </router-link>
      </li>
    </ul>
  </nav>
</template>
<script>
import store from "@/store.js";

export default {
  data() {
    return {
      destinations: store.destinations
    };
  }
};
</script>

<style lang="scss" scoped>
#nav {
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 30px;

  a {
    color: #2c3e50;
    text-decoration: none;
    font-weight: bold;

    &.nav-link-active {
      color: rgb(82, 166, 177);
    }
  }
  .nav-links {
    display: flex;
  }
  .links {
    padding-right: 20px;
    list-style: none;

    &:hover {
      text-decoration: underline;
    }
  }
  .logo {
    font-size: 20px;
    color: #52a6b1;
    font-weight: 300;
  }

  a {
    font-weight: bold;
    color: #2c3e50;
    padding: 0 10px;

    &.nav-link-active {
      color: #3f7a9c;
    }
  }
}
</style>
