---
layout: post
title: "3D Demo! OMG!~"
date: 2023-01-21 18:38:35 +0100
categories: jekyll update
author: "Spy Brightscale"
---

<html>
    <head>
        <meta charset="utf-8">
        <title>My first three.js app</title>
        <style>
            body { margin: 0; }
        </style>
          </head>
    <body>
        <script src="{{site.baseurl}}/scripts/three.js-master/three.js"></script>
    
    <script>
    
            const scene = new THREE.Scene();
            const camera = new THREE.PerspectiveCamera( 75, window.innerWidth / window.innerHeight, 0.1, 1000 );
    
            const renderer = new THREE.WebGLRenderer();
            renderer.setSize( window.innerWidth, window.innerHeight );
      renderer.shadowMap.enabled = true;
renderer.shadowMap.type = THREE.PCFSoftShadowMap;
            document.body.appendChild( renderer.domElement );
    
            const geometry = new THREE.OctahedronGeometry(1.5,1);
            const material = new THREE.MeshLambertMaterial( { color: 0xb64f52});
            const cube = new THREE.Mesh( geometry, material );
            scene.add( cube );
    cube.castShadow = true; //default is false
cube.receiveShadow = true; //default
            camera.position.z = 5;
      camera.position.y = -5;
      camera.rotation.x = 0.7;
      
      const amlight = new THREE.AmbientLight( 0x90643f ); // soft white light
scene.add( amlight );
      const light = new THREE.PointLight( 0xffffff, 1, 100 );
light.position.set( 0, 10, 29 );
light.castShadow = true; // default false
scene.add( light );
      light.shadow.mapSize.width = 4096; // default
light.shadow.mapSize.height = 4096; // default
light.shadow.camera.near = 0.1; // default
light.shadow.camera.far = 500; // default
    
      const planeGeometry = new THREE.PlaneGeometry( 20, 20, 32, 32 );
const planeMaterial = new THREE.MeshStandardMaterial( { color: 0x00ff00 } )
const plane = new THREE.Mesh( planeGeometry, planeMaterial );
plane.receiveShadow = true;
scene.add( plane );
           
      cube.position.z = 2;
      
            function animate() {
                requestAnimationFrame( animate );
    
                cube.rotation.x += 0.01;
                cube.rotation.y += 0.01;
    
                renderer.render( scene, camera );
            };

            animate();
    
    
        </script>
    
    </body>

</html>
