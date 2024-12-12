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

watch(
  () => props.isMarkerCustom,
  (newVal) => {
    if (newVal) {


      const features = handleJson();

      features.forEach((feature) => {
        const el = document.createElement('div');
        el.style.backgroundImage = 'url(https://circlegeo.com/wp-content/uploads/2023/05/Group-15.png)';
        el.style.backgroundSize = 'cover';
        el.style.backgroundRepeat = 'no-repeat';
        el.style.width = '30px';
        el.style.height = '30px';

        const marker = new maplibregl.Marker({ element: el })
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
</script>
