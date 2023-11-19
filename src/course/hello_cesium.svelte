<script>
    import { onMount } from "svelte";
    import * as Cesium from "cesium";
  
    onMount(() => {
      Cesium.Ion.defaultAccessToken =
        "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJqdGkiOiI3YjM2ZjQ1YS0xMDY1LTQzYzEtOWIzYi1kYWY2ODdkY2Q2MTkiLCJpZCI6MTc1NjY1LCJpYXQiOjE2OTg5NDA1MTR9.qNIo1UZjM3M0b206FuWeCG5YeWLMI1r5ASBvhHk5ayg";
      // all API start with the view
        const view = new Cesium.Viewer("cesiumContainer",{
          terrainProvider:Cesium.createWorldTerrain({
            requestWaterMask:true
          })
        });
    });
  </script>
  
  <main>
    <div id="cesiumContainer" />
  </main>
  
  <style>
    #cesiumContainer {
      width: 100vw;
      height: 100vh;
      overflow: hidden;
    }
  </style>
  