<template>
  <div class="details-content">
    <GoBack />
    <div class="destination-wrapper">
      <h1>{{ destination.name }}</h1>
      <div class="destination-details">
        <img
          :src="require(`@/assets/${destination.image}`)"
          alt="destination.name"
        />
        <p>{{ destination.description }}</p>
      </div>
      <div class="experiences">
        <h2>Experiences in {{ destination.name }}</h2>
      </div>
      <div class="cards">
        <div
          v-for="experience in destination.experiences"
          :key="experience.slug"
          class="card"
        >
          <router-link
            :to="{
              name: 'experienceDetails',
              params: { experienceSlug: experience.slug }
            }"
          >
            <img
              :src="require(`@/assets/${experience.image}`)"
              :alt="experience.name"
            />
            <span class="card_text">
              {{ experience.name }}
            </span>
          </router-link>
        </div>
      </div>
      <router-view :key="$route.path" />
    </div>
  </div>
</template>

<script>
import store from "../store.js";
import GoBack from "@/components/GoBack";
export default {
  components: {
    GoBack
  },
  data() {
    return {};
  },
  props: {
    slug: {
      type: String,
      required: true
    }
  },
  computed: {
    destination() {
      return store.destinations.find(
        destination => destination.slug === this.slug
      );
    }
  }
};
</script>

<style lang="scss" scoped>
img {
  max-width: 600px;
  height: auto;
  width: 100%;
  max-height: 400px;
}
.destination-details {
  display: flex;
  justify-content: center;
  padding: 3rem;
}
p {
  margin: 0 40px;
  font-size: 20px;
  text-align: left;
}
.cards {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  .card {
    position: relative;
    padding: 10px;
    cursor: pointer;
    img {
      max-width: 300px !important;
    }
    .card_text {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      color: white;
      font-size: 25px;
      font-weight: bold;
      text-decoration: none;
      opacity: 0;
      transition: opacity 0.2s ease-in;
    }
    &:hover {
      .card_text {
        opacity: 1;
      }
    }
  }
}
</style>
