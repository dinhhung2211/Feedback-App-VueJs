<template>
  <div>
    <feedback-item
      v-for="(feedback, index) in feedbacks"
      :key="index"
      :feedbackData="feedback"
      v-on:deleteFeedback="deleteFeedBack"
    />
  </div>
</template>

<script>
import FeedbackItem from './FeedbackItem.vue'
import { eventBus } from '../main'
import axios from 'axios'

export default {
  data() {
    return {
      feedbacks: [],
      newFeedback: {},
    }
  },
  components: {
    FeedbackItem,
  },
  created() {
    // Get feedbacs
    axios
      .get('http://localhost:5050/feedbacks')
      .then((res) => (this.feedbacks = res.data))
      .catch((err) => console.log(err.message))

    // Get feedbacks to FeedbackStars
    eventBus.$emit('getFeedbacks', this.feedbacks)

    eventBus.$on('addFeedback', (newFeedback) => {
      this.newFeedback = newFeedback
      axios
        .post('http://localhost:5050/feedbacks', newFeedback)
        .then((res) => (this.feedbacks = [res.data, ...this.feedbacks]))
        .catch((err) => console.log(err.message))
    })
    eventBus.$on('editFeedback', (id, newFeedback) => {
      if (id) {
        axios.put(`http://localhost:5050/feedbacks/${id}`, newFeedback)
      }
      this.feedbacks = this.feedbacks.map((item) =>
        item.id === id ? { ...item, ...newFeedback } : item
      )
    })
  },
  methods: {
    deleteFeedBack(id) {
      axios.delete(`http://localhost:5050/feedbacks/${id}`)
      this.feedbacks = this.feedbacks.filter((item) => item.id !== id)
    },
  },
  watch: {
    feedbacks(newValue) {
      eventBus.$emit('getFeedbacks', newValue)
    },
  },
}
</script>

<style></style>
