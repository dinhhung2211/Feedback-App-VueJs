<template>
  <div>
    <Card>
      <template v-slot:children>
        <div class="num-display">{{ feedbackData.rating }}</div>
        <button class="close" @click="$emit('deleteFeedback', feedbackData.id)">
          <font-awesome-icon :icon="['fas', 'trash']" />
        </button>
        <button class="edit" @click="updateFeedback">
          <font-awesome-icon :icon="['fas', 'pen-to-square']" />
        </button>
        <div>{{ feedbackData.text }}</div>
      </template>
    </Card>
  </div>
</template>

<script>
import Card from '../components/shared/Card.vue'
import { eventBus } from '../main'

export default {
  props: {
    feedbackData: Object,
  },
  components: {
    Card,
  },
  methods: {
    updateFeedback() {
      eventBus.$emit('updateFeedback', this.feedbackData)
    },
  },
}
</script>

<style>
.num-display {
  position: absolute;
  top: -10px;
  left: -10px;
}

.close,
.edit {
  position: absolute;
  top: 10px;
  right: 20px;
  cursor: pointer;
  background: none;
  border: none;
}

.edit {
  right: 40px;
}
</style>
