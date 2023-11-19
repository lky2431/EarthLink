<script>
    import { onMount } from "svelte";
    import * as Cesium from "cesium";
  
    onMount(() => {
      Cesium.Ion.defaultAccessToken =
        "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJqdGkiOiI3YjM2ZjQ1YS0xMDY1LTQzYzEtOWIzYi1kYWY2ODdkY2Q2MTkiLCJpZCI6MTc1NjY1LCJpYXQiOjE2OTg5NDA1MTR9.qNIo1UZjM3M0b206FuWeCG5YeWLMI1r5ASBvhHk5ayg";
      // all API start with the view
      const view = new Cesium.Viewer("cesiumContainer", {
        timeline: false,
        animation: false,
        geocoder: false,
        homeButton: false,
        sceneModePicker: false,
        baseLayerPicker: false,
        navigationHelpButton: false,
        fullscreenButton: false,
        infoBox:false,
        selectionIndicator:false
      });
  
  
      const entity = view.entities.add({
        position :Cesium.Cartesian3.fromDegrees(120,30,100),
        billboard:{
          image: '/src/assets/svelte.svg',
          scale: 2.0,
          color: Cesium.Color.BLUE
        },
        label:{
          text:"Hi Hi Hi",
          pixelOffset: new Cesium.Cartesian2(0,40)
        },
        polyline:{
          positions:Cesium.Cartesian3.fromDegreesArrayHeights([120,30,0,120,30,100]),
          material:Cesium.Color.AQUA
        }
  
      })
      view.zoomTo(entity)
  
      
    });
  </script>
  
  <main>
    <div id="cesiumContainer" />
  </main>
  
  <style>
    #cesiumContainer {
      width: 100vw;
      height: 100vh;
      margin: 0;
      padding: 0;
      overflow: hidden;
    }
  </style>
  