# Three.js Cameras Project

## Overview

This project demonstrates the implementation of cameras in Three.js, specifically focusing on PerspectiveCamera and its properties.

## Key Concepts

### PerspectiveCamera

The `THREE.PerspectiveCamera` is used to create a camera that mimics the way human eyes see objects in 3D space.

#### Constructor Parameters:

1. **Field of View (FOV)**: `75` degrees - Controls how wide the camera's view is
2. **Aspect Ratio**: `sizes.width / sizes.height` - Maintains proper proportions
3. **Near Clipping Plane**: `1` - Objects closer than this distance won't be rendered
4. **Far Clipping Plane**: `1000` - Objects farther than this distance won't be rendered

### OrthographicCamera

The `THREE.OrthographicCamera` renders objects without perspective - distant objects appear the same size as near objects. This lacks the natural perspective that human eyes perceive.

#### Constructor Parameters:

```javascript
const camera = new THREE.OrthographicCamera(
  -1 * aspectRatio, // left
  1 * aspectRatio, // right
  1, // top
  -1, // bottom
  0.1, // near
  100 // far
);
```

#### Aspect Ratio Calculation

The renderer size (800x600) is not a perfect square, so using values like `(-1, 1, 1, -1)` would create distortion.

**Why aspect ratio matters:**

- A perfect square viewport would use `(-1, 1, 1, -1)`
- Our viewport is rectangular (800x600), so we calculate `aspectRatio = width/height = 1.333`
- We apply this ratio to the horizontal bounds: `left: -1 * aspectRatio`, `right: 1 * aspectRatio`
- This ensures objects maintain proper proportions without stretching

### Camera Position

```javascript
camera.position.x = 2;
camera.position.y = 2;
camera.position.z = 2;
```

- Sets the camera position in 3D space
- Using positive values moves the camera away from the origin (0,0,0)

### Important Properties and Methods

#### `camera.position.length()`

- **Purpose**: Calculates the distance from the camera to the origin (0,0,0)
- **Use Case**: Useful for debugging camera positioning and understanding spatial relationships
- **Why Used**: Helps verify the camera's distance from the scene center
- **Returns**: A number representing the magnitude of the position vector

#### `camera.lookAt(mesh.position)`

- **Purpose**: Makes the camera point towards a specific object or position
- **Use Case**: Ensures the camera is always focused on the main subject
- **Why Used**: Automatically calculates the proper rotation to face the target

## Code Structure

### Scene Setup

1. Canvas selection and size configuration
2. Scene creation
3. Object creation (red cube with BoxGeometry)
4. Camera setup and positioning
5. Renderer configuration

### Animation Loop

- Uses `THREE.Clock()` for time-based animations
- Rotates the mesh on the Y-axis based on elapsed time
- Continuous rendering with `requestAnimationFrame`

## Technical Notes

### BoxGeometry Parameters

```javascript
new THREE.BoxGeometry(1, 1, 1, 5, 5, 5);
```

- First three parameters: width, height, depth
- Last three parameters: width segments, height segments, depth segments
- More segments create smoother geometry but increase rendering cost

### Renderer Configuration

- `WebGLRenderer` provides hardware-accelerated rendering
- Canvas element must be passed to connect with HTML
- Size must be set to match the canvas dimensions

## Development Tips

1. **Camera Distance**: Use `position.length()` to check if camera is too close/far
2. **Aspect Ratio**: Always calculate dynamically to prevent distortion
3. **Clipping Planes**: Adjust near/far values based on scene scale
4. **LookAt**: Use for automatic camera orientation towards objects

## Future Enhancements

- Implement camera controls (OrbitControls)
- Add multiple camera perspectives
- Implement camera switching
- Add smooth camera transitions
