<template>
  <v-timeline align-top dense>
    <EventListItem v-for="event in events" :key="event"
    :description="event.description"
    :speaker="event.speaker"
    :location="event.location"
    :startTime="event.startTime"
    :endTime="event.endTime"
    >
    </EventListItem>
  </v-timeline>
</template>

<script>
import EventListItem from '@/components/EventListItem.vue'

export default {
  name: 'EventList',
  props: {
    events: {
      type: Array,
      required: true
    }
  },
  components: {
    EventListItem
  }
}
</script>
