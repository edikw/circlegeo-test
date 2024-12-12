<template>
  <div></div>
</template>
<script setup>
import maplibregl from 'maplibre-gl';
import { onMounted, ref, watch } from 'vue';
import gjson from '@/lib/gejson';

const props = defineProps({
  map: { type: Object, required: true },
  isMarkerDefault: { type: Boolean, required: true },
});

const layerId = 'default-marker';
const custom = ref([]);

const handleJson = () => {
  const lineStringFeatures = gjson.features.filter(feature => feature.properties.name === 'Marker Default');

  return lineStringFeatures;
};

watch(() => props.isMarkerDefault, (newVal) => {
  if (newVal) {
    const features = handleJson();
    for (let i = 0; i < features.length; i++) {
      const coordinates = features[i].geometry.coordinates;
      const marker = new maplibregl.Marker()
        .setLngLat(coordinates)
        .setPopup(new maplibregl.Popup().setHTML(`<p>Lat: ${coordinates[1]}</p><p>Long: ${coordinates[0]}</p>`))
        .addTo(props.map);
      custom.value.push(marker);
    }
  } else {
    custom.value.forEach(marker => marker.remove());
    custom.value = [];
  }
});
</script>
