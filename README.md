# Spark Gaussian Splat Demo

An interactive 3D Gaussian Splatting demonstration built with Spark and THREE.js. This demo showcases the power of Gaussian splats with professional cinematography controls, real-time splat manipulation, and seamless integration with traditional 3D meshes.

## What is Gaussian Splatting?

3D Gaussian Splatting (3DGS) is a cutting-edge technique for representing 3D scenes using collections of tiny oriented Gaussian-shaped primitives ("splats"). This enables:
- Photorealistic 3D reconstruction from photos
- Real-time rendering of complex scenes
- Novel view synthesis and 3D content creation

## Demo Features

### Core Functionality
- **Procedural splat generation** - Dynamic spiral and sphere patterns
- **Mixed 3D scenes** - Gaussian splats rendered alongside traditional meshes
- **File format support** - Load .ply, .splat, .ksplat, and .spz files via drag & drop
- **Real-time manipulation** - Scale, flip orientation, and clear splats instantly
- **Spark integration** - Seamless rendering pipeline with THREE.js

### Professional Camera Controls
- **Momentum-based movement** - Smooth acceleration and deceleration
- **Cinematography controls** - Dolly, truck, and lift movements
- **Parallax showcase** - Perfect for demonstrating 3D depth
- **OrbitControls integration** - Mouse orbit and pan functionality

### Interactive Elements
- **Animated clickable cube** - Links to Spark documentation
- **Visual feedback** - Hover effects and cursor changes
- **UI controls** - Buttons for all major functions
- **Live scaling** - Real-time splat size adjustment (0.01x to 10.0x)

## Controls

### Camera Movement (with Momentum)
- **Mouse**: Orbit and pan camera
- **W/S**: Dolly forward/backward (horizontal plane movement)
- **A/D**: Truck left/right (horizontal plane movement) 
- **Q/E**: Lift up/down (Y-axis crane movement)

### Interactions
- **Click animated blue cube**: Opens Spark documentation in new tab
- **Drag & drop splat files**: Instantly load into scene
- **UI buttons**: Access all demo functions
- **Size slider**: Adjust all splats from 0.01x to 10.0x scale

### Splat Management
- **"Add Procedural Splats"**: Generate new spiral and sphere patterns
- **"Flip Splats Y"**: Fix upside-down imported splats
- **"Clear All Splats"**: Remove all splats from scene
- **"Toggle Meshes"**: Show/hide reference cubes and ground plane
- **"Add Axes"**: Generate coordinate axis splats
- **"Reset Camera"**: Return to default view position

## Getting Started

1. **Open the demo** in any modern web browser
2. **Experiment with camera controls** - Use WASD + QE for cinematic movement
3. **Try the truck movement** - Use A/D to slide left/right for beautiful parallax effects
4. **Click the glowing blue cube** - It links to the Spark documentation
5. **Load your own splat files** - Drag and drop .ply or .splat files into the browser
6. **Adjust splat size** - Use the slider to scale all splats in real-time

### Pro Tips for Best Experience

**Showcasing Parallax Effects:**
Use the **A/D truck movement** with the momentum system to create stunning, smooth parallax effects that highlight the 3D depth of Gaussian splats. The momentum creates cinematic camera moves that beautifully demonstrate the volumetric nature of splat-based scenes.

**Momentum System:**
The camera movement includes a realistic momentum system with:
- **Acceleration**: Smooth startup when pressing keys
- **Damping**: Gradual slowdown when releasing keys (85% velocity retention)
- **Max Speed**: Capped for comfortable movement
- **Threshold**: Eliminates tiny jittery movements

**Loading Splat Files:**
- Files are automatically oriented correctly (180° X-axis rotation applied)
- Use "Flip Splats Y" if orientation still appears incorrect
- Multiple files can be loaded and manipulated independently
- All loaded splats respond to the size slider

## Technical Implementation

### Spark Integration
Built on Spark, an advanced 3D Gaussian Splatting renderer for THREE.js:
- **SplatMesh** objects for both loaded files and procedural generation
- **SparkRenderer** manages the splat rendering pipeline
- **Mixed rendering** with traditional THREE.js meshes
- **Automatic sorting** and depth handling

### File Format Support
- **.ply** - Original Gaussian splat format (auto-detected)
- **.spz** - Niantic compressed format (auto-detected)  
- **.splat** - antimatter15/splat format (requires fileType specification)
- **.ksplat** - GaussianSplats3D format (requires fileType specification)

### Performance Features
- **WebGL2 compatible** - Works on 98%+ of modern browsers
- **GPU-accelerated rendering** - Efficient splat processing
- **Mobile device support** - Responsive controls and rendering
- **Memory optimized** - Efficient splat data structures

## Troubleshooting

### Splats Appear Upside Down
The demo automatically applies a 180° rotation around the X-axis to fix common coordinate system issues from photogrammetry/NeRF pipelines. If splats still appear inverted:
1. Use the "Flip Splats Y" button to toggle orientation
2. The rotation is applied per-splat, so you can flip individual loaded files

### Splats Are Too Small/Large
Use the size slider (0.01x to 10.0x) to adjust the scale of all splats in real-time. This affects both loaded and procedural splats.

### Performance Issues
- Try reducing splat file size or complexity
- Close other browser tabs to free up GPU memory
- Check browser console for WebGL errors

### Camera Controls Feel Different
The momentum-based system creates smooth, cinematic movement. If you prefer instant response:
- Hold keys briefly for small movements
- The system responds immediately but smooths acceleration/deceleration

## Requirements

- Modern web browser with WebGL2 support
- No build tools required - runs directly in browser  
- Internet connection for CDN imports
- Recommended: Hardware-accelerated graphics for best performance

## Learn More

- **Spark Documentation**: Click the animated blue cube in the demo
- **Source Code**: View the HTML file to understand implementation
- **Community**: Join the Spark Discord for support and examples

