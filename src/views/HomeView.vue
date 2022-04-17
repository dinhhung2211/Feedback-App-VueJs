<template>
  <div>
    <Header />
    <div class="container">
      <FeedbackForm />
      <FeedbackStars />
      <FeedbackList />
    </div>
    <AboutIconLink />
  </div>
</template>

<script>
// @ is an alias to /src
import Header from '@/components/Header.vue'
import FeedbackForm from '@/components/FeedbackForm.vue'
import FeedbackStars from '@/components/FeedbackStars.vue'
import FeedbackList from '@/components/FeedbackList.vue'
import AboutIconLink from '@/components/AboutIconLink.vue'

export default {
  name: 'HomeView',
  components: {
    Header,
    FeedbackForm,
    FeedbackStars,
    FeedbackList,
    AboutIconLink,
  },
}
</script>
