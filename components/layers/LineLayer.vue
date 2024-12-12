<script setup>
import { onMounted, ref, watch } from 'vue';
import maplibregl from 'maplibre-gl';
import gjson from '@/lib/gejson';

const props = defineProps({
  map: { type: Object, required: true },
});

const layerId = 'line-layer';

const handleJson = () => {
  const lineStringFeatures = gjson.features.filter(feature => feature.geometry.type === 'LineString');
  return lineStringFeatures;
};

onMounted(() => {
  props.map.addSource(layerId, {
    type: 'geojson',
    data: {
      type: 'FeatureCollection',
      features: handleJson(),
    },
  });

  props.map.addLayer({
    id: layerId,
    type: 'line',
    source: layerId,
    paint: {
      'line-color': handleJson()[0].properties.lineColor,
      'line-width': 3,
    },
  });

  props.map.setLayoutProperty(layerId, 'visibility', 'none');

  props.map.on('click', layerId, (e) => {
    const coordinates = e.lngLat;
    new maplibregl.Popup()
      .setLngLat(coordinates)
      .setHTML(`<p>Lat: ${coordinates.lat}</p><p>Long: ${coordinates.lng}</p>`)
      .addTo(props.map);
  });

  props.map.on('mouseenter', layerId, () => {
    props.map.getCanvas().style.cursor = 'pointer';
  });

  props.map.on('mouseleave', layerId, () => {
    props.map.getCanvas().style.cursor = '';
  });
});
</script>
