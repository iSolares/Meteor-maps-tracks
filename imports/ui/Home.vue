
<template>
  <h1 class="">Welcome to Meteor!</h1>
  <div id="map"></div>
</template>

  <script setup>
  import { onMounted, onBeforeMount } from "vue";
  import "leaflet/dist/leaflet.css"
  import L, { icon } from 'leaflet'

  let map = null
  let markers = []
  const myIcon = L.icon({
   iconUrl: 'myIcon.png',
   // ...
});
  const createMap = () => {
    map = L.map('map').setView([-12.943959872367998, -38.425812701465304], 5)
    L.tileLayer('https://tile.openstreetmap.org/{z}/{x}/{y}.png', {
      attribution: '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'
    }).addTo(map)
    L.marker([-12.943959872367998, -38.425812701465304], {icon: myIcon}).addTo(map);
    if(markers.length) {
      setMarkers()
    }
  }

  const setMarkers = () => {
    markers.map((marker) =>{
      return L.marker([marker])
    })
  }
  onMounted(() => {
    createMap()
  })
  onBeforeMount(() => {
    if(map) {
      map.remove
    }
  })
  </script>

  <style>
#map {
   height: 1000px; 
}
</style>