<template>
  <div>
    <span class="go-back">
      <button @click="goBack">Go Back</button>
    </span>
  </div>
</template>

<script>
export default {
  methods: {
    goBack() {
      return this.$router.go(-1);
    }
  }
};
</script>
<style lang="scss" scoped>
.go-back {
  display: flex;
  justify-content: center;
  cursor: pointer;

  button {
    border: 1px solid;
    padding: 10px 30px;
    outline: 0;
    font-size: 14px;
  }
}
</style>
