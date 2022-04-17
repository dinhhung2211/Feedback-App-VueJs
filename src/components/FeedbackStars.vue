<template>
  <div class="feedback-stats">
    <h4>{{ feedbacks.length }} Reviews</h4>
    <h4>Average Rating: {{ average }}</h4>
  </div>
</template>

<script>
import { eventBus } from '../main'

export default {
  data() {
    return {
      feedbacks: [],
      average: 0,
    }
  },
  created() {
    eventBus.$on('getFeedbacks', (feedbacks) => {
      this.feedbacks = feedbacks
      if (this.feedbacks.length > 0) {
        this.average =
          feedbacks.reduce((acc, cur) => {
            return Number(acc) + Number(cur.rating)
          }, 0) / feedbacks.length
        this.average = this.average.toFixed(1).replace(/[.,]0$/, '')
      } else {
        this.average = 0
      }
    })
  },
  watch: {
    feedbacks(newValue) {
      this.feedbacks = newValue
      if (this.feedbacks.length > 0) {
        this.average =
          newValue.reduce((acc, cur) => {
            return Number(acc) + Number(cur.rating)
          }, 0) / newValue.length
        this.average = this.average.toFixed(1).replace(/[.,]0$/, '')
      } else {
        this.average = 0
      }
    },
  },
}
</script>

<style>
.feedback-stats {
  color: #fff;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
</style>
