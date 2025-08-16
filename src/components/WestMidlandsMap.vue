<!-- components/WestMidlandsMap.vue -->
<script setup lang="ts">
import { LMap, LTileLayer, LMarker, LPopup } from '@vue-leaflet/vue-leaflet'

// West Midlands-ish center (Birmingham)
const center: [number, number] = [52.4862, -1.8904]  // lat, lng
const zoom = 9

// Replace/extend with your real coverage areas
const areas = [
    // Major boroughs / cities
    { name: 'Birmingham', lat: 52.4862, lng: -1.8904 },
    { name: 'Coventry', lat: 52.4068, lng: -1.5197 },
    { name: 'Dudley', lat: 52.5123, lng: -2.0810 },
    { name: 'Sandwell', lat: 52.5187, lng: -1.9945 },
    { name: 'Solihull', lat: 52.4143, lng: -1.7809 },
    { name: 'Walsall', lat: 52.5862, lng: -1.9829 },
    { name: 'Wolverhampton', lat: 52.5862, lng: -2.1280 },

    // Birmingham suburbs & adjacent towns
    { name: 'Sutton Coldfield', lat: 52.5667, lng: -1.8167 },
    { name: 'Aston', lat: 52.5096, lng: -1.8885 },
    { name: 'Edgbaston', lat: 52.4612, lng: -1.9330 },
    { name: 'Harborne', lat: 52.4600, lng: -1.9575 },
    { name: 'Handsworth', lat: 52.5173, lng: -1.9144 },

    // Dudley borough towns
    { name: 'Stourbridge', lat: 52.4582, lng: -2.1250 },
    { name: 'Halesowen', lat: 52.4445, lng: -2.0463 },
    { name: 'Kingswinford', lat: 52.5186, lng: -2.1171 },
    { name: 'Coseley', lat: 52.5118, lng: -2.1292 },

    // Sandwell borough towns
    { name: 'West Bromwich', lat: 52.5187, lng: -1.9945 },
    { name: 'Smethwick', lat: 52.4995, lng: -1.9980 },
    { name: 'Oldbury', lat: 52.5018, lng: -2.0158 },
    { name: 'Rowley Regis', lat: 52.5124, lng: -2.0412 },
    { name: 'Tipton', lat: 52.5171, lng: -2.0536 },
    { name: 'Wednesbury', lat: 52.5544, lng: -2.0154 },

    // Solihull borough towns/parishes
    { name: 'Balsall Common', lat: 52.4038, lng: -1.6646 },
    { name: 'Knowle', lat: 52.3619, lng: -1.7265 },
    { name: 'Castle Bromwich', lat: 52.4934, lng: -1.8223 },
    { name: 'Chelmsley Wood', lat: 52.4957, lng: -1.6760 },
    { name: 'Marston Green', lat: 52.4611, lng: -1.7858 },
    { name: 'Solihull Town', lat: 52.4128, lng: -1.7787 },

    // Walsall borough towns
    { name: 'Bloxwich', lat: 52.6103, lng: -1.9645 },
    { name: 'Bilston', lat: 52.5600, lng: -2.0629 },
    { name: 'Walsall Town', lat: 52.5833, lng: -2.0000 },
    { name: 'Aldridge', lat: 52.6245, lng: -1.8740 },

    // Wolverhampton borough towns
    { name: 'Bilston', lat: 52.5600, lng: -2.0629 },
    { name: 'Wednesfield', lat: 52.6076, lng: -2.0800 },
    { name: 'Tettenhall', lat: 52.5885, lng: -2.1490 },
    { name: 'Compton', lat: 52.5910, lng: -2.1550 }
];


// Optional: compute bounds to fit all pins
const bounds = [
    [Math.min(...areas.map(a => a.lat)), Math.min(...areas.map(a => a.lng))],
    [Math.max(...areas.map(a => a.lat)), Math.max(...areas.map(a => a.lng))]
] as [[number, number], [number, number]]
</script>

<template>
    <!-- Client-only to avoid SSR DOM issues -->
    <ClientOnly>
        <LMap :use-global-leaflet="false" :zoom="zoom" :center="center" :max-zoom="18"
            style="height: 450px; width: 100%;" :bounds="bounds" :bounds-padding="[40, 40]">
            <LTileLayer url="https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png"
                attribution="&copy; OpenStreetMap contributors" />
            <LMarker v-for="a in areas" :key="a.name" :lat-lng="[a.lat, a.lng]">
                <LPopup>
                    <strong>{{ a.name }}</strong><br />
                    Covered by Rehaligned
                </LPopup>
            </LMarker>
        </LMap>
    </ClientOnly>
</template>
