# Project 01 - First Three.js Scene

## What I Built

Basic Three.js scene with a spinning cube.

## Key Concepts

- **Scene**: Container for all 3D objects
- **Camera**: Defines viewpoint (PerspectiveCamera)
- **Renderer**: Draws the scene (WebGLRenderer)
- **Geometry**: Shape definition (BoxGeometry)
- **Material**: Surface appearance (MeshBasicMaterial)
- **Mesh**: Geometry + Material

## Code Structure

```javascript
// Basic setup pattern
const scene = new THREE.Scene();
const camera = new THREE.PerspectiveCamera();
const renderer = new THREE.WebGLRenderer();

// Create object
const geometry = new THREE.BoxGeometry();
const material = new THREE.MeshBasicMaterial();
const mesh = new THREE.Mesh(geometry, material);

// Render
renderer.render(scene, camera);
```
