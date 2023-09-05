<script setup>
import { ref, onMounted } from 'vue'
import EventService from '@/services/EventService.js'

const props = defineProps({
  id: {
    required: true,
  },
})
const event = ref(null)

onMounted(() => {
  EventService.getEvent(props.id)
    .then((res) => {
      event.value = res.data
    })
    .catch((e) => console.log(e))
})
</script>

<template>
  <div v-if="event">
    <h1>{{ event.title }}</h1>
    <span>{{ event.time }} on {{ event.date }} @ {{ event.location }}</span>
    <p>{{ event.description }}</p>
  </div>
</template>
