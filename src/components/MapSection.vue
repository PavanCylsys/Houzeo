<template>
  <div ref="mapContainer" class="w-full h-full"></div>
</template>

<script>
import L from "leaflet";
import "leaflet/dist/leaflet.css";

export default {
  name: "WorldMap",
  mounted() {
    const map = L.map(this.$refs.mapContainer,{zoomControl: false}).setView([20, 0], 2); // World view

    L.tileLayer("https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png", {
      attribution: "© OpenStreetMap contributors",
    }).addTo(map);

    // Example marker
    L.marker([19.076, 72.8777]) // Mumbai
      .addTo(map)
      .bindPopup("Mumbai");
  },
};
</script>

<style>
/* Fix Leaflet icon issue */
.leaflet-container {
  height: 100%;
  width: 100%;
}
</style>
