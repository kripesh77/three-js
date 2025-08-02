# Project 05 - Animations

## What I Built

Creating smooth animations using Three.js animation loops.

## Key Concepts

- **requestAnimationFrame**: Browser-optimized animation loop
- **Clock**: Three.js time tracking utility
- **Delta time**: Time between frames for smooth animation
- **Easing**: Making animations feel natural
- **Performance**: Keeping 60fps target

## Code Patterns

```javascript
// Basic animation loop
const tick = () => {
  // Update objects
  mesh.rotation.y += 0.01;

  // Render
  renderer.render(scene, camera);

  // Call tick again on next frame
  window.requestAnimationFrame(tick);
};
tick();

// Using Clock for time-based animation
const clock = new THREE.Clock();

const tick = () => {
  const elapsedTime = clock.getElapsedTime();

  // Time-based rotation (consistent speed)
  mesh.rotation.y = elapsedTime;

  renderer.render(scene, camera);
  window.requestAnimationFrame(tick);
};
```
