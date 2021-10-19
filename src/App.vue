<template>
  <div id="app">
    <div class="button-container">
      <button @click="back">回退</button>
      <button @click="clear">清空</button>
      <button @click="save">导出</button>
    </div>
    <div id="map-container">
      <baidu-map
          class="bm-view"
          ak="自己的ak"
          :scroll-wheel-zoom="true"
          :center="center"
          :zoom="zoom"
          @ready="handler"
      @click="clickMap">
        <!--  折线  -->
        <bm-polyline :path="polylinePath" stroke-color="blue" :stroke-opacity="0.5" :stroke-weight="2"></bm-polyline>
      </baidu-map>
    </div>
  </div>
</template>

<script>
import { saveAs } from 'file-saver';
import BaiduMap from 'vue-baidu-map/components/map/Map.vue'
import BmPolyline from 'vue-baidu-map/components/overlays/Polyline.vue'
export default {
  name: 'App',
  components: {
    BaiduMap,BmPolyline
  },
  data () {
    return {
      center: {lng: 0, lat: 0},
      zoom: 3,
      markerPoint: { lng: 106.210442, lat: 38.295465 },
      polylinePath: []
    }
  },
  methods: {
    handler () {
      this.center.lng = 106.210442
      this.center.lat = 38.295465
      this.zoom = 10
    },
    clickMap({ type, point }) {
      console.log(type)
      this.polylinePath.push({lat: point.lat, lng: point.lng})
    },
    back() {
      this.polylinePath.splice(this.polylinePath.length-1, 1)
    },
    clear() { this.polylinePath = [] },
    save() {
      const blob = new Blob([JSON.stringify(this.polylinePath)], {type: "application/json"});
      saveAs(blob, "111.json");
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 20px;
  width: 100%;
  height: calc(100% - 20px);
  background-color: white;
}
.button-container {
  height: 50px;
}
#map-container {
  height: calc(100% - 50px);

}
.bm-view {
  width: 100%;
  height: 100%;
  background-color: white;
}

</style>
