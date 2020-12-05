---
title: LMapboxVectorTileLayer
---

# LMapboxVectorTileLayer

> Load tiles from a map server and display them accordingly to map zoom, center and size

---

## Demo

::: demo
<template>
<l-map style="height: 350px" :zoom="zoom" :center="center">
<l-mapbox-vector-tile-layer :styleUrl="styleUrl"></l-mapbox-vector-tile-layer>
</l-map>
</template>

<script>
import { LMap, LTileLayer, LMapboxVectorTileLayer } from 'vue2-leaflet';

export default {
  components: { LMap, LTileLayer, LMapboxVectorTileLayer },
  data() {
    return {
      url: 'https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png',
      zoom: 8,
      center: [47.313220, -1.319482],
      styleUrl: 'http://localhost:8900',
    };
  },
};
</script>

:::

## Props

| Prop name                  | Description                                          | Type          | Values | Default    |
| -------------------------- | ---------------------------------------------------- | ------------- | ------ | ---------- |
| options                    | Leaflet options to pass to the component constructor | object        | -      | {}         |
| pane                       |                                                      | string        | -      | 'tilePane' |
| attribution                |                                                      | string        | -      | null       |
| name                       |                                                      | string        | -      | undefined  |
| layerType                  |                                                      | string        | -      | undefined  |
| visible                    |                                                      | boolean       | -      | true       |
| opacity                    |                                                      | number        | -      | 1.0        |
| zIndex                     |                                                      | number        | -      | 1          |
| tileSize                   |                                                      | number        | -      | 256        |
| noWrap                     |                                                      | boolean       | -      | false      |
| tms                        |                                                      | boolean       | -      | false      |
| subdomains                 |                                                      | string\|array | -      | 'abc'      |
| detectRetina               |                                                      | boolean       | -      | false      |
| url                        |                                                      | string        | -      | null       |
| styleUrl                   |                                                      | string        | -      | null       |
| mapboxVectorTileLayerClass |                                                      | func          | -      | L.mapboxGL |

## Events

| Event name     | Properties                                               | Description                                        |
| -------------- | -------------------------------------------------------- | -------------------------------------------------- |
| update:visible | **value** `boolean` - value of the visible property      | Triggers when the visible prop needs to be updated |
| ready          | **mapObject** `object` - reference to leaflet map object | Triggers when the component is ready               |
