# Spark Gaussian Splat Demos

Welcome to the Spark demos! Spark is an advanced 3D Gaussian Splatting renderer for THREE.js that allows you to seamlessly integrate Gaussian splats with traditional mesh-based 3D scenes.

## What is Gaussian Splatting?

3D Gaussian Splatting (3DGS) is a cutting-edge technique for representing 3D scenes using collections of tiny oriented Gaussian-shaped primitives ("splats"). This enables:
- Photorealistic 3D reconstruction from photos
- Real-time rendering of complex scenes
- Novel view synthesis and 3D content creation

## Demo Files

### 1. `spark-gaussian-splat-demo.html` - Complete Demo
**Features:**
- Procedural splat generation (spiral and sphere patterns)
- Mixed scenes with both splats and traditional meshes
- Drag & drop support for .ply, .splat, .ksplat, and .spz files
- Splat orientation fixer (fixes upside-down imports)
- Real-time splat size control with slider
- Clear all splats functionality
- Interactive controls (mouse orbit, WASD movement)
- UI controls for adding/toggling different elements

**Controls:**
- Mouse: Orbit camera
- W/S: Move forward/backward
- A/D: Move left/right  
- Q/E: Move up/down (Y-axis)
- Drag & drop splat files onto the window
- Use "Flip Splats Y" if imported splats appear upside-down
- Adjust splat size with the slider (0.01x to 10.0x)
- Use buttons to add procedural content

### 2. `simple-spark-demo.html` - Minimal Example
**Features:**
- Basic Spark setup with THREE.js
- Simple procedural splat creation
- Animated rotating splat pattern
- Perfect starting point for learning

## Key Spark Concepts

### SplatMesh
The core object for Gaussian splats in Spark:
```javascript
const splats = new SplatMesh({
    url: "./my-splat-file.ply",  // Load from file
    // OR
    constructSplats: (splats) => {
        // Create splats procedurally
        splats.addSplat({
            center: [x, y, z],
            scale: [sx, sy, sz],
            color: [r, g, b],
            opacity: opacity,
            quaternion: [x, y, z, w]
        });
    }
});
```

### SparkRenderer
Manages the splat rendering pipeline:
```javascript
const spark = new SparkRenderer({ 
    renderer: threeRenderer,
    autoUpdate: true 
});
camera.add(spark);  // Follow camera for precision
```

### File Format Support
Spark supports multiple splat formats:
- **.ply** - Original Gaussian splat format (auto-detected)
- **.spz** - Niantic compressed format (auto-detected)
- **.splat** - antimatter15/splat format (needs fileType specified)
- **.ksplat** - GaussianSplats3D format (needs fileType specified)

## Integration Benefits

### Seamless THREE.js Integration
- SplatMesh extends THREE.Object3D
- Works with existing THREE.js scenes and pipelines
- Correct depth sorting with traditional meshes
- Standard transformations (position, rotation, scale)

### Performance
- WebGL2 compatible (98%+ browser support)
- GPU-accelerated rendering
- Mobile device support
- Efficient memory usage

### Programmable
- Procedural splat generation
- Real-time splat editing and animation
- Shader graph system (Dyno) for advanced effects
- Multiple viewpoint rendering

## Getting Started

1. **Open either demo file** in a modern web browser
2. **Experiment with the controls** to understand the interaction
3. **Try loading your own splat files** via drag & drop
4. **View the source code** to understand the implementation
5. **Modify the examples** to create your own scenes

## Next Steps

- Visit the [Spark documentation](https://sparkjs.dev) for complete API reference
- Join the [Spark Discord](https://discord.gg/W39qmSKemS) community
- Check out the React examples in the community resources
- Experiment with the Dyno shader graph system for advanced effects

## Requirements

- Modern web browser with WebGL2 support
- No build tools required - runs directly in browser
- Internet connection for CDN imports

## Troubleshooting

### Splats Appear Upside Down
Many Gaussian splat files come from photogrammetry/NeRF pipelines that use different coordinate systems than THREE.js. The demo automatically applies a 180° rotation around the X-axis to fix this, but if splats still appear inverted:
1. Use the "Flip Splats Y" button to toggle orientation
2. The rotation is applied per-splat, so you can flip individual loaded files

### Splats Are Too Small/Large
Use the size slider (0.1x to 3.0x) to adjust the scale of all splats in real-time. This affects both loaded and procedural splats.

### Performance Issues
- Try reducing splat file size or complexity
- Close other browser tabs to free up GPU memory
- Check browser console for WebGL errors

