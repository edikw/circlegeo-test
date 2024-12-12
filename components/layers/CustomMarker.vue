<script setup>
import maplibregl from 'maplibre-gl';
import { onMounted, ref, watch } from 'vue';
import gjson from '@/lib/gejson';

const props = defineProps({
  map: { type: Object, required: true },
  isMarkerCustom: { type: Boolean, required: true },
});

const customMarkers = ref([]);

const handleJson = () => {
  return gjson.features.filter(
    (feature) => feature.properties.name === 'Custom Image Marker'
  );
};

onMounted(() => {
  watch(
    () => props.isMarkerCustom,
    (newVal) => {
      if (newVal) {
        const features = handleJson();

        features.forEach((feature) => {
          const markerImage = '/images/logo.png';

          const el = document.createElement('div');
          el.style.backgroundImage = `url(${markerImage})`;
          el.style.width = '40px';
          el.style.height = '40px';
          el.style.backgroundSize = 'cover';

          const marker = new maplibregl.Marker(el)
            .setLngLat(feature.geometry.coordinates)
            .setPopup(
              new maplibregl.Popup().setHTML(
                `<p>Coordinates: ${feature.geometry.coordinates}</p>`
              )
            )
            .addTo(props.map);

          customMarkers.value.push(marker);
        });
      } else {
        customMarkers.value.forEach((marker) => marker.remove());
        customMarkers.value = [];
      }
    },
    { immediate: true }
  );
});
</script>
