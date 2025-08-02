# Project 04 - Transform Objects

## What I Built

Working with object transformations - position, rotation, and scale.

## Key Concepts

- **Position**: Moving objects in 3D space (x, y, z)
- **Rotation**: Rotating objects around axes (Euler angles)
- **Scale**: Resizing objects uniformly or per axis
- **Object3D**: Base class with transform properties
- **Vector3**: For position and scale values
- **Euler**: For rotation values

## Code Patterns

```javascript
// Position
mesh.position.x = 1;
mesh.position.set(x, y, z);

// Rotation (in radians)
mesh.rotation.y = Math.PI * 0.25;
mesh.rotation.set(x, y, z);

// Scale
mesh.scale.x = 2;
mesh.scale.set(x, y, z);

// Distance and normalization
console.log(mesh.position.length()); // distance from origin
mesh.position.normalize(); // make length = 1
```
