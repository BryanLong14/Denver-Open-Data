<template>
   <div class=" row ">
      <div class="col-md-10 ">
        <div id="map" class="map"></div>
        <!-- Denver Open Data Map will be rendered here -->
      </div>
      <div class="col-md-2 ">
        <!-- The layer checkboxes will be rendered here -->
      </div>
    </div>
</template>

<script>
export default {
  name: "BaseMap",
  props: {
    msg: String
  },
  data: {
    map: null,
    tileLayer: null,
    layers: [
      {
        id: 0,
        name: "Crime",
        active: false,
        features: [
          // import crome data as an object here. EX: {
          //   id: 0,
          //   name: 'Bogart\'s Smokehouse',
          //   type: 'marker',
          //   coords: [38.6109607, -90.2050322],
          // },
        ]
      }
    ]
  },
  mounted() {
    this.initMap();
    this.initLayers();
  },
  methods: {
    initMap() {
      this.map = L.map("map").setView([39.7392, -104.9903], 14);
      this.tileLayer = L.tileLayer("https://korona.geog.uni-heidelberg.de/tiles/roads/x={x}&y={y}&z={z}", {
        attribution:
          'Imagery from <a href="http://giscience.uni-hd.de/">GIS</a> Map data &copy; <a href="http://www.openstreetmap.org/copyright">OpenStreetMap</a>',
        maxZoom: 20,
        attribution:
          '&copy; <a href="http://www.openstreetmap.org/copyright">OpenStreetMap</a>, &copy; <a href="https://carto.com/attribution">CARTO</a>'
      });
      this.tileLayer.addTo(this.map);
    },
    initLayers() {}
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.map {
  height: 90vh;
}
</style>
