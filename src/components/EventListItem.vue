<template>
  <div class="event-list-item">
    <div class="start-time">{{ weekdayShortName(startTime) }}, {{ timeToString(startTime) }}</div>
    <div class="left-padded">
      <div class="description">{{ description }}</div>
    </div>
    <div v-if="speaker != null" class="left-padded">
      <div class="speaker">&#x1f464; {{ speaker }}</div>
    </div>
    <div v-if="location != null || endTime != null" class="left-padded top-margin">
      <div v-if="location != null" class="location">{{ location }}</div>
      <div v-if="endTime != null" class="duration">{{ durationToString(endTime-startTime) }}</div>
      <div v-if="endTime != null" class="end-time"> &rarr; {{ timeToString(endTime) }}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "EventListItem",
  props: {
    description: {
      type: String,
      required: true
    },
    speaker: {
      type: String,
      required: false
    },
    location: {
      type: String,
      required: false
    },
    startTime: {
      type: Date,
      required: true
    },
    endTime: {
      type: Date,
      required: false
    }
  },
  methods: {
    weekdayShortName(date) {
      return ["So", "Mo", "Di", "Mi", "Do", "Fr", "Sa"][date.getDay()]
    },
    timeToString(time) {
      return time == null ? "" : time.getHours() + ":" + (time.getMinutes() < 10 ? "0" : "") + time.getMinutes() + " Uhr"
    },
    durationToString(millis) {
      var minutes = Math.round(millis / 60000)
      var hours = Math.floor(minutes / 60)
      minutes -= 60 * hours
      var resultList = []
      if (hours > 0) {
        resultList.push(hours + "h")
      }
      if (minutes > 0 || resultList.length == 0) {
        resultList.push(minutes + "min")
      }
      return resultList.join(" ")
    }
  }
}
</script>

<style>
.event-list-item {
  margin: 3em;
  position: relative;
  text-align: left;
}
.start-time {
  position: absolute;
  font-size: 150%;
}
.top-margin {
  margin-top: 0.75em;
}
.left-padded {
  padding-left: 12em;
}
.left-padded div {
  margin-right: 1em;
}
.description {
  display: inline;
  font-size: 150%;
  font-weight: bold;
}
.speaker {
  display: inline;
}
.location {
  display: inline;
  background-color: green;
  border: green 0.25em solid;
  border-radius: 0.5em;
  color: white;
  white-space: nowrap;
}
.duration {
  display: inline;
  background-color: #095375;
  border: #095375 0.25em solid;
  border-radius: 0.5em;
  color: white;
  white-space: nowrap;
}
.end-time {
  display: inline;
  background-color: #56c8fd;
  border: #56c8fd 0.25em solid;
  border-radius: 0.5em;
  white-space: nowrap;
}
</style>
