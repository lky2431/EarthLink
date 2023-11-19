<script>
    import { onMount } from "svelte";
    import * as Cesium from "cesium";
  
    onMount(() => {
      Cesium.Ion.defaultAccessToken =
        "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJqdGkiOiI3YjM2ZjQ1YS0xMDY1LTQzYzEtOWIzYi1kYWY2ODdkY2Q2MTkiLCJpZCI6MTc1NjY1LCJpYXQiOjE2OTg5NDA1MTR9.qNIo1UZjM3M0b206FuWeCG5YeWLMI1r5ASBvhHk5ayg";
      // all API start with the view
      const view = new Cesium.Viewer("cesiumContainer");
  
  
      const billboard = view.entities.add({
        position :Cesium.Cartesian3.fromDegrees(116,40),
        billboard:{
          image: '/src/assets/svelte.svg',
          scale: 2.0,
          color: Cesium.Color.BLUE
        },
      })
  
      const label = view.entities.add({
        position: Cesium.Cartesian3.fromDegrees(112,30),
        label:{
          text:"Cesium",
          fillColor: Cesium.Color.RED,
          showBackground: true,
          backgroundColor: new Cesium.Color(0,0,50)
        }
      })
      view.zoomTo(billboard)
  
      
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
  