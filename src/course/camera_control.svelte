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
        });
        const position = Cesium.Cartesian3.fromDegrees(110, 20, 20000);
        view.camera.setView({
            destination: position,
            orientation: {
                // default (0,-90,0)
                heading: Cesium.Math.toRadians(0),
                pitch: Cesium.Math.toRadians(0),
                roll: Cesium.Math.toRadians(0),
            },
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
        margin: 0;
        padding: 0;
        overflow: hidden;
    }
</style>
