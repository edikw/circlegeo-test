<template>
  <div>
    <div>
      <h1 class=" font-bold mb-4 cursor-pointer w-max" @click.prevent="$router.go(-1)">&#8592; Bagian B</h1>
    </div>
    <div ref="mapContainer" class="map-container"></div>
    <div class="flex gap-2 flex-wrap justify-center gap-2 my-6">
      <button :class="handleActive('line-layer') ? 'btn' : 'btn-border'" @click="toggleLayer('line-layer')"> Line
        Layer</button>
      <button :class="handleActive('polygon-layer') ? 'btn' : 'btn-border'" @click="toggleLayer('polygon-layer')">
        Polygon Layer</button>
      <button :class="handleActive('circle-source') ? 'btn' : 'btn-border'" @click="toggleLayer('circle-source')">
        Circle
        Layer</button>
      <button :class="handleActive('custom-marker') ? 'btn' : 'btn-border'" @click="toggleLayer('custom-marker')">
        Custom Marker</button>
      <button :class="handleActive('default-marker') ? 'btn' : 'btn-border'" @click="toggleLayer('default-marker')">
        Default Marker</button>
      <button :class="handleActive('terrain-data') ? 'btn' : 'btn-border'" @click="toggleLayer('terrain-data')">
        Vector Line Layer</button>
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


const config = useRuntimeConfig();
const apiKey = config.public.KEY;

const mapContainer = ref(null);
const map = ref(null);
const isMapReady = ref(false);
const isMarkerCustom = ref(false);
const isMarkerDefault = ref(false);
const activeLayers = ref([]);
const setZoom = ref(4);

const handleActive = (layerId) => {
  return activeLayers.value.includes(layerId);
};

const toggleLayer = (layerId) => {
  if (!map.value) return;

  if (activeLayers.value.includes(layerId)) {
    activeLayers.value = activeLayers.value.filter((id) => id !== layerId);
  } else {
    activeLayers.value = [...activeLayers.value, layerId];
  }

  if (activeLayers.value.length === 1 && activeLayers.value[0] === 'terrain-data' && layerId === 'terrain-data') {
    map.value.flyTo({
      center: [106.8456, -6.2088],
      zoom: 14,
    });
  } else {
    map.value.flyTo({
      center: [106.8456, -6.2088],
      zoom: 4,
    });
  }


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
    // bisa pilih salah satu dari style berikut
    style: 'https://basemaps.cartocdn.com/gl/positron-gl-style/style.json',
    // style: 'https://demotiles.maplibre.org/style.json',
    // style: `https://api.maptiler.com/maps/streets/style.json?key=${apiKey}`,
    center: [106.8456, -6.2088],
    zoom: 4,
  });

  map.value.on('load', () => {
    isMapReady.value = true;
  });
});
</script>

<style scoped>
.map-container {
  width: 100%;
  height: 75vh;
}
</style>
