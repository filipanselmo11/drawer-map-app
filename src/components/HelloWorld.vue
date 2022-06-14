<template>
  <div id="map"></div>
</template>

<script>
import "leaflet/dist/leaflet.css";
import "leaflet";
import "leaflet-draw/dist/leaflet.draw.css";
import "leaflet-draw";
const L = window['L'];
var drawnItems = new L.FeatureGroup();
var drawControl = new L.Control.Draw({
  edit: {
    featureGroup: drawnItems,
  },
});
export default {
  name: "HelloWorld",
  data: () => ({
    map: undefined,
  }),
  mounted() {
    this.initMap();
  },
  methods: {
    initMap() {
      this.map = L.map("map", { drawControl: true }).setView([51.505, -0.09], 13);
      L.tileLayer("http://{s}.tile.osm.org/{z}/{x}/{y}.png", {
        attribution:
          '&copy; <a href="http://osm.org/copyright">OpenStreetMap</a> contributors',
      }).addTo(this.map);
      this.map.addLayer(drawnItems);
      this.map.addControl(drawControl);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
