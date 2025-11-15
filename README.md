# VR Gaussian Splat Viewer

A web-based VR viewer for 3D Gaussian Splats, optimized for smartphone users with VR headsets.

## Features

- 📱 **Mobile VR Support**: Works with Google Cardboard and other mobile VR headsets
- 🥽 **WebXR Compatible**: Supports modern VR headsets (Quest, etc.)
- 🎮 **Desktop Preview**: View and interact with the splat on desktop browsers
- 🚀 **No Installation Required**: Pure web-based, no apps needed

## How to Use

### On Desktop
1. Open `index.html` in a modern browser (Chrome, Firefox, Edge)
2. Click and drag to rotate the view
3. Use mouse wheel to zoom

### On Mobile VR (Google Cardboard, etc.)
1. Open `index.html` in a WebXR-compatible mobile browser:
   - **Chrome** (recommended)
   - **Firefox Reality**
   - **Samsung Internet**
2. Wait for the Gaussian splat to load
3. Click the "Enter VR" button
4. Insert your phone into your VR headset
5. Look around to explore the 3D scene

### On VR Headsets (Quest, etc.)
1. Open the built-in browser on your VR headset
2. Navigate to the hosted URL
3. Click "Enter VR" to start the immersive experience

## Technical Details

### Libraries Used
- **Three.js v0.160**: 3D rendering engine
- **@mkkellogg/gaussian-splats-3d**: Gaussian splatting renderer with WebXR support
- **WebXR API**: Virtual reality support

### Sample Data
The viewer loads a sample Gaussian splat (bonsai scene) from HuggingFace. You can replace this with your own `.ply` or `.splat` files by modifying the `splatUrl` in `index.html`.

### Browser Compatibility
- ✅ Chrome/Edge (Desktop & Mobile)
- ✅ Firefox (Desktop & Mobile)
- ✅ Safari (Limited VR support)
- ✅ Quest Browser
- ✅ Pico Browser

## Hosting

To use this with a VR headset, you'll need to host the file:

### Option 1: Local Server
```bash
# Python 3
python -m http.server 8000

# Then visit: http://localhost:8000
```

### Option 2: GitHub Pages
1. Push to GitHub
2. Enable GitHub Pages in repository settings
3. Access via `https://yourusername.github.io/reponame/`

### Option 3: Netlify/Vercel
- Drag and drop the folder to Netlify Drop or Vercel

## Customization

### Load Your Own Gaussian Splat
Edit `index.html` and change the `splatUrl`:

```javascript
const splatUrl = 'path/to/your/point_cloud.ply';
```

### Adjust Camera Position
Modify the initial camera settings:

```javascript
viewer = new GaussianSplats3D.Viewer({
    initialCameraPosition: [-1, -4, 6],  // [x, y, z]
    initialCameraLookAt: [0, 4, 0],      // [x, y, z]
    // ...
});
```

### Change Scale and Position
Adjust the splat scene parameters:

```javascript
await viewer.addSplatScene(splatUrl, {
    position: [0, 1, 0],      // [x, y, z]
    scale: [1.5, 1.5, 1.5],   // [x, y, z]
    rotation: [0, 0, 0, 1]     // quaternion [x, y, z, w]
});
```

## Troubleshooting

### "VR Not Supported" message
- Ensure you're using a WebXR-compatible browser
- Try Chrome or Firefox on your mobile device
- Some browsers require HTTPS for VR features

### Splat not loading
- Check your internet connection
- Open browser console (F12) to see error messages
- Try a different sample splat URL

### Performance issues
- Reduce the scale of the splat
- Use a device with better GPU
- Close other applications

## Resources

- [GaussianSplats3D Documentation](https://github.com/mkkellogg/GaussianSplats3D)
- [WebXR Device API](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
- [Free Gaussian Splat Samples](https://huggingface.co/datasets/dylanebert/3dgs)

## License

This project uses open-source libraries. Please check individual library licenses.
