/* eslint-disable */
<template>
  <h1>Events For Good</h1>
  <div class="events">
    <EventCard v-for="event11 in events" :key="event11.id" :event="event11" />
  </div>
</template>

<script>
// @ is an alias to /src
import EventCard from '@/components/EventCard.vue'
import EventService from '@/services/EventService.js'

export default {
  name: 'EventList',
  components: {
    EventCard,
  },
  data() {
    return {
      events: null,
    }
  },
  created() {
    EventService.getEvents()
      .then((response) => {
        this.events = response.data
        console.log('events:', response.data)
      })
      .catch((e) => {
        console.log(e)
      })
  },
}
</script>

<style scoped>
.events {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
