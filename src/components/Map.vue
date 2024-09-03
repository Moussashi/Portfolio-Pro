<template>
    <div id="map">
        <l-map
            :center="center"
            :zoom="zoom"
            ref="map"
            id="map"
            @update:center="centerUpdated"
            @update:zoom="zoomUpdated">
            <l-tile-layer
            :url="url"></l-tile-layer>
            <l-marker
                :key="markers[0].id"
                :lat-lng="markers[0].coords"></l-marker>

        </l-map>
    </div>
</template>

<script>
import { LMap, LTileLayer, LMarker } from "@vue-leaflet/vue-leaflet";
import { Icon } from 'leaflet';

delete Icon.Default.prototype._getIconUrl;
Icon.Default.mergeOptions({
  iconRetinaUrl: require('leaflet/dist/images/marker-icon-2x.png'),
  iconUrl: require('leaflet/dist/images/marker-icon.png'),
  shadowUrl: require('leaflet/dist/images/marker-shadow.png'),
});
export default {
    components: {
        LMap,
        LTileLayer,
        LMarker,
    },
    data() {
        return {
            url: 'https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png',
            center: [48.8112109986514, 2.2977432786115464],
            zoom: 12,
            markers: [
                {
                    id: 1,
                    coodrs: [-21.22245743980369, 55.303528173890086] // Not real marker
                }
            ]

        }
    },
    methods: {
        centerUpdated(center) {
            this.center = center
        },
        zoomUpdated(zoom) {
            this.zoom = zoom
        }
    },
}
</script>