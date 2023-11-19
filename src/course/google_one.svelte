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
      
      viewer = new Cesium.Viewer("cesiumContainer", {
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
  
      const tileset = viewer.scene.primitives.add(new Cesium.Cesium3DTileset({
        url: "https://tile.googleapis.com/v1/3dtiles/root.json?key=AIzaSyA-s60coLqfZsD2xahUoa0wuy_6kHEi9eA",
        showCreditsOnScreen: true,
        enableDebugWireframe:true
      }));
      
  
      viewer.scene.globe.show = false;
      const position = Cesium.Cartesian3.fromDegrees(114.1694,22.319, 20000);
      viewer.camera.setView({
              destination: position,
              orientation: {
                  // default (0,-90,0)
                  heading: Cesium.Math.toRadians(0),
                  pitch: Cesium.Math.toRadians(-90),
                  roll: Cesium.Math.toRadians(0),
              },
          });
  
  
      
  
  
      
    });
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
  