<template>
  <div />
</template>

<script>
import { optionsMerger, propsBinder, findRealParent } from '../utils/utils.js';
import Options from '../mixins/Options.js';
import { DomEvent } from 'leaflet';
import 'mapbox-gl-leaflet';
import { MapboxVectorTileLayerMixin } from '../index';

/**
 * Load tiles from a map server and display them accordingly to map zoom, center and size
 */
export default {
  name: 'LMapboxVectorTileLayer',
  mixins: [MapboxVectorTileLayerMixin, Options],
  props: {
    url: {
      type: String,
      default: null,
    },
    styleUrl: {
      type: String,
      default: null,
    },
    mapboxVectorTileLayerClass: {
      type: Function,
      default: L.mapboxGL,
    },
  },
  mounted() {
    const options = optionsMerger(this.tileLayerOptions, this);
    this.mapObject = this.mapboxVectorTileLayerClass({
      style: this.styleUrl,
      ...options,
    });
    DomEvent.on(this.mapObject, this.$listeners);
    propsBinder(this, this.mapObject, this.$options.props);
    this.parentContainer = findRealParent(this.$parent);
    this.parentContainer.addLayer(this, !this.visible);
    this.$nextTick(() => {
      /**
       * Triggers when the component is ready
       * @type {object}
       * @property {object} mapObject - reference to leaflet map object
       */
      this.$emit('ready', this.mapObject);
    });
  },
};
</script>

<docs>
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
</docs>
