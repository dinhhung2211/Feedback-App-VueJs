<template>
  <card>
    <template v-slot:children>
      <form @submit.prevent="handleSubmit">
        <h2>Bạn đánh giá như thế nào về dịch vụ của chúng tôi?</h2>
        <rating-select :rating="rating" @ratingChanged="rating = $event" />
        <div class="input-group">
          <input
            v-model="feedbackContent"
            type="text"
            placeholder="Viết đánh giá"
          />
          <button type="submit" class="btn btn-secondary">Gửi</button>
        </div>
      </form>
    </template>
  </card>
</template>

<script>
import Card from '../components/shared/Card.vue'
import RatingSelect from './RatingSelect.vue'
import { eventBus } from '../main'

export default {
  data() {
    return {
      id: '',
      feedbackContent: '',
      rating: 5,
      edit: false,
    }
  },
  created() {
    eventBus.$on('updateFeedback', (feedbackData) => {
      this.id = feedbackData.id
      this.feedbackContent = feedbackData.text
      this.rating = feedbackData.rating
      this.edit = true
    })
  },
  methods: {
    handleSubmit() {
      const newFeedback = {
        text: this.feedbackContent,
        rating: this.rating,
      }

      if (this.edit === true) {
        eventBus.$emit('editFeedback', this.id, newFeedback)
      } else {
        // send to list data
        eventBus.$emit('addFeedback', newFeedback)
      }

      this.feedbackContent = ''
    },
  },
  components: {
    Card,
    RatingSelect,
  },
}
</script>

<style>
.card h2 {
  font-size: 22px;
  font-weight: 600;
  text-align: center;
}

.input-group {
  display: flex;
  flex-direction: row;
  border: 1px solid #ccc;
  padding: 8px 10px;
  border-radius: 8px;
}

input {
  flex-grow: 1;
  border: none;
  font-size: 16px;
}

input:focus {
  outline: none;
}

.btn {
  color: #fff;
  border: 0;
  border-radius: 8px;
  color: #fff;
  width: 100px;
  height: 40px;
  cursor: pointer;
}

.btn-primary {
  background-color: #202142;
}

.btn-secondary {
  background: #ff6a95;
}

.btn:hover {
  transform: scale(0.98);
  opacity: 0.9;
}

.btn:disabled {
  background-color: #cccccc;
  color: #333;
  cursor: auto;
}

.btn:disabled:hover {
  transform: scale(1);
  opacity: 1;
}
</style>
