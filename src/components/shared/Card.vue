<template>
  <div class="card">
    <slot name="children"></slot>
  </div>
</template>

<script>
export default {}
</script>

<style scoped>
.card {
  background-color: #fff;
  color: #333;
  border-radius: 15px;
  padding: 40px 50px;
  margin: 20px 0;
  position: relative;
}
</style>
