<script setup>
import { onMounted, ref } from 'vue';
import maplibregl from 'maplibre-gl';

const props = defineProps({
  map: { type: Object, required: true },

});

const layerId = 'terrain-data';

onMounted(() => {
  if (props.map) {
    props.map.addSource('contours', {
      type: 'vector',
      url: 'https://api.maptiler.com/tiles/contours/tiles.json?key=G5RlpCUY2cSj7PbF2Ca8',
    });

    props.map.addLayer({
      'id': 'terrain-data',
      'type': 'line',
      'source': 'contours',
      'source-layer': 'contour',
      'layout': {
        'line-join': 'round',
        'line-cap': 'round'
      },
      'paint': {
        'line-color': 'red',
        'line-width': 2
      }
    });
  }
})
</script>
