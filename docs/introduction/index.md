<!DOCTYPE html>
<html lang="el">
  <head>
    <meta charset="utf-8" />
    <title>AR.js + A-Frame Demo</title>
    <!-- A-Frame library -->
    <script src="https://aframe.io/releases/1.4.0/aframe.min.js"></script>
    <!-- AR.js for A-Frame -->
    <script src="https://raw.githack.com/AR-js-org/AR.js/master/aframe/build/aframe-ar.js"></script>
    <style>
      body { margin: 0; overflow: hidden; }
    </style>
  </head>
  <body>
    <!-- Σκηνή με ενεργοποιημένο το AR.js -->
    <a-scene embedded arjs="sourceType: webcam; debugUIEnabled: false;">
      
      <!-- Marker “hiro” -->
      <a-marker preset="hiro">
        <!-- Φόρτωση και εμφάνιση του 3D μοντέλου -->
        <a-entity 
          gltf-model="#myModel" 
          scale="0.5 0.5 0.5" 
          animation-mixer>
        </a-entity>
      </a-marker>

      <!-- Camera -->
      <a-entity camera></a-entity>

      <!-- Προαιρετικό φόντο AR -->
      <a-entity light="type: ambient; intensity: 0.5"></a-entity>
      <a-entity light="type: directional; intensity: 0.8" position="1 1 0"></a-entity>

    </a-scene>

    <!-- Αssets section -->
    <a-assets>
      <a-asset-item id="myModel" src="assets/model.gltf"></a-asset-item>
    </a-assets>
  </body>
</html>

