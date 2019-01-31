<template>
  <div id="app">
    <h1>h4rdc0d3rz' w0rksh4pp</h1>
    <EventList :events="events"></EventList>
  </div>
</template>

<script>
import EventList from "@/components/EventList.vue"

export default {
  name: "app",
  data() {
    return {
      name: "",
      description: "",
      events: [
        { speaker: null, description: "Wanderung", location: "Wald", startTime: new Date("2019-06-19T18:00:00+02:00"), endTime: new Date("2019-06-19T21:00:00+02:00") },
        { speaker: null, description: "Party", location: "Bar", startTime: new Date("2019-06-19T18:00:00+02:00"), endTime: null },
        { speaker: null, description: "Frühstück", location: "Buffet", startTime: new Date("2019-06-20T07:30:00+02:00"), endTime: new Date("2019-06-20T09:15:00+02:00") },
        { speaker: "Anton Angermeier", description: "Eröffnungsrede", location: "Plenum", startTime: new Date("2019-06-20T09:30:00+02:00"), endTime: new Date("2019-06-20T09:45:00+02:00") },
        { speaker: "Berta Baumann", description: "Historischer Rückblick", location: "Plenum", startTime: new Date("2019-06-20T09:45:00+02:00"), endTime: new Date("2019-06-20T10:45:00+02:00") },
        { speaker: "Chris Carlsson", description: "Aktuelle Entwicklungen", location: "Plenum", startTime: new Date("2019-06-20T10:45:00+02:00"), endTime: new Date("2019-06-20T11:45:00+02:00") },
        { speaker: null, description: "Mittagspause", location: "Buffet", startTime: new Date("2019-06-20T11:45:00+02:00"), endTime: new Date("2019-06-20T13:00:00+02:00") },
        { speaker: "Doris Decker", description: "Erfahrungen aus dem Sport", location: "Raum 4", startTime: new Date("2019-06-20T13:00:00+02:00"), endTime: new Date("2019-06-20T14:00:00+02:00") },
        { speaker: "Emil Eismann", description: "Erfahrungen aus der Wirtschaft", location: "Raum 3", startTime: new Date("2019-06-20T13:00:00+02:00"), endTime: new Date("2019-06-20T14:00:00+02:00") },
        { speaker: "Franziska Fungo", description: "Erfahrungen aus der Natur", location: "Raum 2", startTime: new Date("2019-06-20T14:15:00+02:00"), endTime: new Date("2019-06-20T15:15:00+02:00") },
        { speaker: "Gerd Grundmann", description: "Erfahrungen vom Bau", location: "Raum 3", startTime: new Date("2019-06-20T14:15:00+02:00"), endTime: new Date("2019-06-20T15:15:00+02:00") },
        { speaker: null, description: "Kaffeepause", location: "Café", startTime: new Date("2019-06-20T15:15:00+02:00"), endTime: new Date("2019-06-20T16:00:00+02:00") },
        { speaker: null, description: "Abendveranstaltung - Überraschung ;-)", location: "wird noch bekanntgegeben", startTime: new Date("2019-06-20T17:00:00+02:00"), endTime: new Date("2019-06-20T20:00:00+02:00") },
        { speaker: null, description: "Frühstück", location: "Buffet", startTime: new Date("2019-06-21T07:30:00+02:00"), endTime: new Date("2019-06-21T09:15:00+02:00") },
        { speaker: "Hannelore Hempel", description: "Die Zukunft im Blick", location: "Plenum", startTime: new Date("2019-06-21T09:30:00+02:00"), endTime: new Date("2019-06-21T10:30:00+02:00") },
        { speaker: "Ingo Insauer", description: "Erfahrungen aus der Wissenschaft", location: "Raum 2", startTime: new Date("2019-06-21T10:45:00+02:00"), endTime: new Date("2019-06-21T11:45:00+02:00") },
        { speaker: "Jana Jäger", description: "Erfahrungen aus der Musik", location: "Raum 4", startTime: new Date("2019-06-21T10:45:00+02:00"), endTime: new Date("2019-06-21T11:45:00+02:00") },
        { speaker: "Karl Klammer", description: "Erfahrungen aus der Kunst", location: "Raum 3", startTime: new Date("2019-06-21T10:45:00+02:00"), endTime: new Date("2019-06-21T11:45:00+02:00") },
        { speaker: null, description: "Mittagspause", location: "Buffet", startTime: new Date("2019-06-21T11:45:00+02:00"), endTime: new Date("2019-06-21T13:00:00+02:00") },
        { speaker: "Laura Lindner", description: "Das beste Best-Of aller Zeiten", location: "Plenum", startTime: new Date("2019-06-21T13:00:00+02:00"), endTime: new Date("2019-06-21T14:00:00+02:00") },
        { speaker: "Anton Angermeier", description: "Zusammenfassung und Abschluss", location: "Plenum", startTime: new Date("2019-06-21T14:00:00+02:00"), endTime: new Date("2019-06-21T14:30:00+02:00") },
      ],
      signedIn: false
    };
  },
  components: {
    EventList
  }
};
</script>

<style>
body {
  margin: 0;
}
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.container {
  padding: 40px;
}
.signout {
  background-color: #ededed;
  margin: 0;
  padding: 11px 0px 1px;
}
</style>
