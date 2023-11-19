<script>
    import { onMount } from "svelte";
    import * as Cesium from "cesium";
    let view
  
  
  
    const toDel= ()=>{
      //view.entities.remove();
  
      //view.entities.removeAll();
  
      //view.entities.removeById();
  
      
    }
  
    onMount(() => {
      Cesium.Ion.defaultAccessToken =
        "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJqdGkiOiI3YjM2ZjQ1YS0xMDY1LTQzYzEtOWIzYi1kYWY2ODdkY2Q2MTkiLCJpZCI6MTc1NjY1LCJpYXQiOjE2OTg5NDA1MTR9.qNIo1UZjM3M0b206FuWeCG5YeWLMI1r5ASBvhHk5ayg";
      // all API start with the view
      view = new Cesium.Viewer("cesiumContainer", {
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
  
      const point = view.entities.add({
        position: Cesium.Cartesian3.fromDegrees(121,30),
        point:{
          color:Cesium.Color.BLUE,
          pixelSize:20
        }
      })
      view.zoomTo(point)
  
  
      
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
  