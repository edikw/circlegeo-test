<script setup>
import { onMounted, ref } from 'vue';

const props = defineProps({
  map: { type: Object, required: true },
});

const isVisible = ref(true);
const layerId = 'vector-line-layer';

onMounted(() => {

  // Tambahkan sumber data vector tiles
  props.map.addSource('vector-source', {
    type: 'vector',
    tiles: ['https://rami.bmkg.go.id/api/windtemp_get/wafc/WT/snow/850/202405121800/202405131200/{z}/{x}/{y}.png'],
    minzoom: 0,
    maxzoom: 14,
  });

  // Tambahkan layer ke peta
  props.map.addLayer({
    id: layerId,
    type: 'line',
    source: 'vector-source',
    'source-layer': 'line-layer', // Nama source-layer dari Vector Tiles
    paint: {
      'line-color': '#0000FF',
      'line-width': 2,
    },
  });
});
</script>

<style scoped>
.toggle-layer {
  position: fixed;
  top: 10px;
  left: 10px;
  z-index: 1000;
}
</style>
