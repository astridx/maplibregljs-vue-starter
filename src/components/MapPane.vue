<script setup lang="ts">
import 'maplibre-gl/dist/maplibre-gl.css'
import { Map, NavigationControl } from 'maplibre-gl'
import { onMounted } from 'vue'

import '@maplibre/maplibre-gl-compare/dist/maplibre-gl-compare.css'
import Compare from '@/lib/Compare';

onMounted(() => {
  var beforeMap = new Map({
    container: "before",
    style: "https://demotiles.maplibre.org/style.json",
    center: [7.221275, 50.326111],
    zoom: 5,
  });

  var afterMap = new Map({
    container: "after",
    style:
      "https://vectortiles.geo.admin.ch/styles/ch.swisstopo.leichte-basiskarte.vt/style.json",
    center: [7.221275, 50.326111],
    zoom: 5,
  });

  var container = "#comparison-container";

  var map = new Compare(beforeMap, afterMap, container, {
  });
})
</script>

<template>
  <div id="comparison-container">
    <div id="before" class="map"></div>
    <div id="after" class="map"></div>
  </div>
</template>

<style scoped>
.map {
  position: absolute;
  top: 0;
  bottom: 0;
  width: 100%;
}
</style>
