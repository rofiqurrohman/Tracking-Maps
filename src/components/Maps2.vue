<template>
  <l-map style="height: 100vh" :zoom="zoom" :center="center">
    <l-tile-layer :url="url" :attribution="attribution"></l-tile-layer>
    <l-marker :lat-lng="center">
      <l-icon :icon-size="dynamicSize" :icon-anchor="dynamicAnchor" :icon-url="require('../assets/truck.png')" />
    </l-marker>
  </l-map>
</template>

<script>
import L from 'leaflet';
// eslint-disable-next-line object-curly-newline
import { LMap, LTileLayer, LMarker, LIcon } from 'vue2-leaflet';

export default {
  components: {
    LMap,
    LTileLayer,
    LMarker,
    // eslint-disable-next-line vue/no-unused-components
    LIcon,
  },
  data() {
    return {
      url: 'https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png',
      attribution: '&copy; <a target="_blank" href="http://osm.org/copyright">OpenStreetMap</a> contributors',
      zoom: 15,
      center: [-8.9872716, 116.763545],
      iconSize: 50,
    };
  },
  computed: {
    dynamicSize() {
      return [this.iconSize, this.iconSize * 1.15];
    },
    dynamicAnchor() {
      return [this.iconSize / 2, this.iconSize * 1.15];
    },
  },
};
</script>
