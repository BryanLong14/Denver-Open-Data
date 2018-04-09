<template>
  <div class=" row ">
    <div class="col-md-9">
    <div id="map" class="map">  
    </div>
    <!-- Denver Open Data Map will be rendered here -->
    </div>
    <div class="col-md-3">
     <!-- The layer checkboxes will be rendered here -->
    <div
    class="form-check"
    v-for="layer in layers"
    :key="layer.id"
    >
    <label class="form-check-label">
    <input
    class="form-check-input"
    type="checkbox"
    v-model="layer.active"
    @change="layerChanged(layer.id, layer.active)"
    />
    {{ layer.name }}
    </label>
    </div>
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
          {
            id: "20181388",
            name: "auto-theft",
            type: "marker",
            coords: [39.7770144, -104.8046632]
          },
          {
            id: "20181016",
            name: "auto-theft",
            type: "marker",
            coords: [39.7633303, -104.9305771]
          },
          {
            id: "20181498",
            name: "larceny",
            type: "marker",
            coords: [39.739432, -104.9631267]
          },
          {
            id: "20181388",
            name: "auto-theft",
            type: "marker",
            coords: [39.7770144, -104.8046632]
          },
          {
            id: "20181016",
            name: "auto-theft",
            type: "marker",
            coords: [39.7633303, -104.9305771]
          },
          {
            id: "20181498",
            name: "larceny",
            type: "marker",
            coords: [39.739432, -104.9631267]
          },
          {
            id: "20181388",
            name: "auto-theft",
            type: "marker",
            coords: [39.7771134, -104.8046432]
          },
          {
            id: "20181016",
            name: "auto-theft",
            type: "marker",
            coords: [39.7633203, -104.9305671]
          },
          {
            id: "20181498",
            name: "larceny",
            type: "marker",
            coords: [39.739332, -104.963147]
          }
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
      this.tileLayer = L.tileLayer(
        "https://korona.geog.uni-heidelberg.de/tiles/roads/x={x}&y={y}&z={z}",
        {
          attribution:
            'Imagery from <a href="http://giscience.uni-hd.de/">GIS</a> Map data &copy; <a href="http://www.openstreetmap.org/copyright">OpenStreetMap</a>',
          maxZoom: 20,
          attribution:
            '&copy; <a href="http://www.openstreetmap.org/copyright">OpenStreetMap</a>, &copy; <a href="https://carto.com/attribution">CARTO</a>'
        }
      );
      this.tileLayer.addTo(this.map);
    },
    initLayers() {
      this.layers.forEach(layer => {
        const markerFeature = layer.features.filter(feature => feature.type === "marker");
      });
      markerFeature.forEach(feature => {
        feature.leafletObject = L.marker(feature.coords).bindPopup(feature.name);
      });
    },
    layerChanged(layerId, active) {
      const layer = this.layers.find(layer => layer.id === layerId);
      layer.features.forEach(feature => {
        if (active) {
          feature.leafletObject.addTo(this.map);
        } else {
          feature.leafletObject.removerFrom(this.map);
        }
      });
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.map {
  height: 100vh;
}
</style>
