<template>
  <div class="container">
    <card>
      <template v-slot:children>
        <div class="about">
          <h1>About This Project</h1>
          <p>Đây là Feedback App được viết bằng VueJS</p>
          <p>Author: Hung Truong</p>
          <p>Version: 1.0.0</p>
          <p><router-link to="/">Back To Home</router-link></p>
        </div>
      </template>
    </card>
  </div>
</template>

<script>
import Card from '@/components/shared/Card.vue'

export default {
  components: {
    Card,
  },
}
</script>

<style>
.container {
  max-width: 768px;
  margin: auto;
  padding: 0 20px;
}

.about h1 {
  margin-bottom: 20px;
}

.about p {
  margin: 10px 0;
}
</style>
