<template>
  <div class="home">
    <h1 class="maintitle">Treavel Destination</h1>
    <div class="destination-wrapper">
      <div v-for="destination in destinations" :key="destination.name">
        <router-link
          class="router-link"
          :to="{
            name: 'DestinationDetails',
            params: { slug: destination.slug }
          }"
        >
          <h2>{{ destination.name }}</h2>
        </router-link>
        <figure>
          <router-link
            :to="{
              name: 'DestinationDetails',
              params: { slug: destination.slug }
            }"
          >
            <img :src="require(`@/assets/${destination.image}`)" alt="" />
          </router-link>
        </figure>
      </div>
    </div>
  </div>
</template>

<script>
import store from "../store.js";
export default {
  name: "home",
  components: {},
  data() {
    return {
      destinations: store.destinations
    };
  }
};
</script>
<style lang="scss" scope>
.home {
  max-width: 1400px;
  margin: 0 auto;
}
.destination-wrapper {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;

  img {
    width: 420px;
  }
  .router-link {
    text-decoration: none;
    h2 {
      color: #3f7a9c;
      transition: color 0.2s ease-in;
      &:hover {
        color: #52a6b1;
      }
    }
  }
}
</style>
