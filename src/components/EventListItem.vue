<template>
  <v-timeline-item fill-dot>
    <v-card class="event-list-item">
      <div class="start-time">
        {{ startWeekdayShort }}, {{ startTimeString }}
      </div>
      <div class="left-padded">
        <div class="description">{{ description }}</div>
      </div>
      <div v-if="speaker != null" class="left-padded">
        <div class="speaker"><v-icon>person</v-icon> {{ speaker }}</div>
      </div>
      <div v-if="location != null || endTime != null" class="left-padded top-margin">
        <div v-if="location != null" class="location">{{ location }}</div>
        <div v-if="endTime != null" class="duration">{{ durationString }}</div>
        <div v-if="endTime != null" class="end-time"> &rarr; {{ endTimeString }}</div>
      </div>
    </v-card>
  </v-timeline-item>
</template>

<script>
export default {
  name: 'EventListItem',
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
    weekdayShort (date) {
      return ['So', 'Mo', 'Di', 'Mi', 'Do', 'Fr', 'Sa'][date.getDay()]
    },
    timeToString (time) {
      return time == null ? '' : time.getHours() + ':' + (time.getMinutes() < 10 ? '0' : '') + time.getMinutes() + ' Uhr'
    },
    durationToString (millis) {
      var minutes = Math.round(millis / 60000)
      var hours = Math.floor(minutes / 60)
      minutes -= 60 * hours
      var resultList = []
      if (hours > 0) {
        resultList.push(hours + 'h')
      }
      if (minutes > 0 || !resultList) {
        resultList.push(minutes + 'min')
      }
      return resultList.join(' ')
    }
  },
  computed: {
    startTimeString: function () {
      return this.timeToString(this.startTime)
    },
    endTimeString: function () {
      return this.timeToString(this.endTime)
    },
    startWeekdayShort: function () {
      return this.weekdayShort(this.startTime)
    },
    durationString: function () {
      if (this.endTime != null && this.startTime <= this.endTime) {
        return this.durationToString(this.endTime - this.startTime)
      }
      return ''
    }
  }
}
</script>

<style>
.event-list-item {
  padding: 0.5em;
  position: relative;
  text-align: left;
  max-width: 50em;
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
