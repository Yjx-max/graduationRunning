<script>
import { onMounted } from "vue";
import leaflet  from "leaflet";
import imgUrl from './icon/sdu.jpg'
export default {
    name: "maps",
}
</script>

<script setup>
let mymap;
        onMounted(() => {

            var map
            map = leaflet.map('map', {
                crs: leaflet.CRS.Simple
            }).setView([0, -40], 2);
            var imageUrl = imgUrl,
                imageBounds = [[-108, -154.7], [108, 154.7]];
            leaflet.imageOverlay(imageUrl, imageBounds).addTo(map)
            var myIcon = leaflet.divIcon({
                className: 'my-div-icon',
                html: '<div style="width: 30px; height: 30px; background-color: white;"></div>'
            });
            leaflet.marker([50, 30], {icon: myIcon}).addTo(map);

            // leaflet.marker([0, 0]).addTo(map).bindPopup("I am the position1.");



        });

</script>

<template>
    <div id="map"></div>
</template>

<style>
#map {
    height: 100%;
    width: 100%;
}
</style>
<!-- 
npm i leaflet -->