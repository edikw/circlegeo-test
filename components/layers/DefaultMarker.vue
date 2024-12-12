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

onMounted(() => {
  watch(() => props.isMarkerDefault, () => {
    if (props.isMarkerDefault) {
      for (let i = 0; i < handleJson().length; i++) {
        const marker = new maplibregl.Marker()
          .setLngLat(handleJson()[i].geometry.coordinates)
          .setPopup(new maplibregl.Popup().setHTML('<p>' + handleJson()[i].geometry.coordinates + '</p>'))
          .addTo(props.map);
        custom.value.push(marker);
      }
    } else {
      custom.value.forEach(marker => marker.remove());
      custom.value = [];
    }
  });
});
</script>
