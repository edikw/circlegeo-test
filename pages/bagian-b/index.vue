<template>
  <div>
    <div>
      <h1 class=" font-bold mb-4 cursor-pointer w-max" @click.prevent="$router.go(-1)">&#8592; Bagian B</h1>
    </div>
    <div ref="mapContainer" class="map-container"></div>
    <div class="flex gap-2 my-6 justify-center">
      <button class="btn" @click="toggleLayer('line-layer')"> Line Layer</button>
      <button class="btn" @click="toggleLayer('polygon-layer')"> Polygon Layer</button>
      <button class="btn" @click="toggleLayer('circle-source')"> Circle Layer</button>
      <button class="btn" @click="toggleLayer('custom-marker')"> Custom Marker</button>
      <button class="btn" @click="toggleLayer('default-marker')"> Default Marker</button>
      <button class="btn" @click="toggleLayer('vector-line-layer')"> Vector Line Layer</button>
    </div>


    <div v-if="isMapReady" style="display:flex;">
      <LineLayer :map="map" />
      <PolygonLayer :map="map" />
      <CircleLayer :map="map" />
      <CustomMarker :isMarkerCustom="isMarkerCustom" :map="map" />
      <DefaultMarker :isMarkerDefault="isMarkerDefault" :map="map" />
      <VectorLine :map="map" />
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, defineEmits } from 'vue';
import maplibregl from 'maplibre-gl';

const mapContainer = ref(null);
const map = ref(null);
const isMapReady = ref(false);
const isMarkerCustom = ref(false);
const isMarkerDefault = ref(false);


const toggleLayer = (layerId) => {
  if (!map.value) return;
  if (layerId === 'custom-marker') {
    isMarkerCustom.value = !isMarkerCustom.value;
  }
  else if (layerId === 'default-marker') {
    isMarkerDefault.value = !isMarkerDefault.value;
  } else {
    const isVisible = map.value.getLayoutProperty(layerId, 'visibility') === 'visible';
    map.value.setLayoutProperty(layerId, 'visibility', isVisible ? 'none' : 'visible');
  }
};

onMounted(() => {
  map.value = new maplibregl.Map({
    container: mapContainer.value,
    style: 'https://demotiles.maplibre.org/style.json',
    center: [106.8456, -6.2088],
    zoom: 3,
  });
  map.value.on('load', () => {
    isMapReady.value = true;
  });
});
</script>

<style scoped>
.map-container {
  width: 100%;
  height: 80vh;
}
</style>
