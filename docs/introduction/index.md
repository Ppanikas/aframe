<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Απλό Ηλιακό Σύστημα - A-Frame</title>
    <script src="https://aframe.io/releases/1.5.0/aframe.min.js"></script>
  </head>
  <body>
    <a-scene background="color: black">
      <!-- Ήλιος -->
      <a-sphere position="0 1.5 -5" radius="1" color="orange" 
                animation="property: rotation; to: 0 360 0; loop: true; dur: 10000"></a-sphere>

      <!-- Γη -->
      <a-sphere position="3 1.5 -5" radius="0.5" color="blue"
                animation="property: rotation; to: 0 360 0; loop: true; dur: 5000"></a-sphere>

      <!-- Κείμενο -->
      <a-text value="Απλό Ηλιακό Σύστημα" position="-2 3 -4" color="#FFFFFF"></a-text>

      <!-- Κάμερα -->
      <a-entity camera look-controls position="0 1.6 0"></a-entity>
    </a-scene>
  </body>
</html>
