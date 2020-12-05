---
pageClass: example-page
---

# Mapbox Vector Tile Layers

::: tip
Use layer symbol on the top right to select which layer you
want to display. More information about WMS (Web Map Service) can be
found on the [leaflet.js WMS example page](http://leafletjs.com/examples/wms/wms.html)
:::

::: demo
<template>
  <l-map style="height: 350px" :zoom="zoom" :center="center">
    <l-mapbox-vector-tile-layer :styleUrl="styleUrl"></l-mapbox-vector-tile-layer>
  </l-map>
</template>

<script>
import {LMap, LTileLayer, LMapboxVectorTileLayer} from 'vue2-leaflet';

export default {
  components: { LMap, LTileLayer, LMapboxVectorTileLayer},
  data () {
    return {
      url: 'https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png',
      zoom: 8,
      center: [38.03, 114.48],
      styleUrl: 'http://localhost:8900/static/style/osm_liberty/osm_liberty.json',
    };
  }
}
</script>

:::
