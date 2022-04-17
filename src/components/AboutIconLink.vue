<template>
  <div class="about-link">
    <router-link to="/about"
      ><font-awesome-icon :icon="['fas', 'circle-question']"
    /></router-link>
  </div>
</template>

<script>
export default {}
</script>

<style>
.about-link {
  position: fixed;
  bottom: 20px;
  right: 30px;
  color: #fff;
  cursor: pointer;
  font-size: 40px;
}

.about-link a {
  color: #fff;
}

.about-link a:hover {
  color: #ff6a95;
}
</style>
