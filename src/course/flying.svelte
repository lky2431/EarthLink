<script>
  import { onMount } from "svelte";
  import * as Cesium from "cesium";
  let viewer



  const toDel= ()=>{
    //view.entities.remove();

    //view.entities.removeAll();

    //view.entities.removeById();

    
  }

  onMount(() => {
    
    Cesium.Ion.defaultAccessToken =
        "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJqdGkiOiI3YjM2ZjQ1YS0xMDY1LTQzYzEtOWIzYi1kYWY2ODdkY2Q2MTkiLCJpZCI6MTc1NjY1LCJpYXQiOjE2OTg5NDA1MTR9.qNIo1UZjM3M0b206FuWeCG5YeWLMI1r5ASBvhHk5ayg";
      // all API start with the view
      const viewer = new Cesium.Viewer("cesiumContainer", {
        terrainProvider:Cesium.createWorldTerrain(),
        timeline: false,
        animation: false,
        geocoder: false,
        homeButton: false,
        sceneModePicker: false,
        baseLayerPicker: false,
        navigationHelpButton: false,
        fullscreenButton: false,
      });
      viewer.extend(Cesium.viewerCesium3DTilesInspectorMixin);

      const position = Cesium.Cartesian3.fromDegrees(110, 20, 20000);
      viewer.camera.flyTo({
        destination: position,
        orientation: {
          heading: Cesium.Math.toRadians(0),
          pitch: Cesium.Math.toRadians(-90),
          roll: Cesium.Math.toRadians(0),
        },
        duration: 3,
      });
  
      const position2 = Cesium.Cartesian3.fromDegrees(110, 20);
      viewer.camera.lookAt(
        position,
        new Cesium.HeadingPitchRange(
          Cesium.Math.toRadians(0),
          Cesium.Math.toRadians(-90),
          20000
        )
      );
    })
</script>

<main>
  <div id="cesiumContainer" />
  <button on:click={toDel}>
    Click to Delete
  </button>
</main>

<style>
  #cesiumContainer {
    width: 100vw;
    height: 100vh;
    margin: 0;
    padding: 0;
    overflow: hidden;
  }

  button{
    position: absolute;
    top:50px;
    left: 50px;
    z-index: 999;
  }
</style>
