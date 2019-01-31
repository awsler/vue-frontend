<template>
  <div>
    <div v-for="event in events" :key="event">
      <EventListItem
      :description="event.description"
      :speaker="event.speaker"
      :location="event.location"
      :startTime="event.startTime"
      :endTime="event.endTime"
      >
      </EventListItem>
    </div>
  </div>
</template>

<script>
import EventListItem from "@/components/EventListItem.vue"

export default {
  name: "EventList",
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
