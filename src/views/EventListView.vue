<script setup>
import EventCard from '@/components/EventCard.vue'
import { ref, onMounted } from 'vue'
import EventService from

const events = ref(null)

onMounted(() => {
  axios
    .get(
      'https://my-json-server.typicode.com/agathelurquin/real-world-vue-3-db/events'
    )
    .then((res) => {
      console.log('events:', res)
      events.value = res.data
    })
    .catch((error) => {
      console.log(error)
    })
})
</script>

<template>
  <h1>Events For Good</h1>
  <div class="events">
    <EventCard v-for="event in events" :key="event.id" :event="event" />
  </div>
</template>

<style scoped>
.events {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
