# STUDIFY — Image to Roblox Stud 3D

A static, dependency-free website that turns images into **real studded 2.5D geometry** for Roblox Studio. No backend, API keys, AI, or Blender required.

## Try it

Open [`index.html`](./index.html) in a modern browser, or publish the repository using GitHub Pages (Deploy from branch → `main` → `/root`).

1. Upload a PNG, JPG, or WebP.
2. **Drag a rectangle** on the image to isolate the subject. For reference sheets, crop the character rather than the entire page.
3. Choose stud resolution, depth, color palette, background removal and stud shape.
4. Rotate / zoom the WebGL preview.
5. Click **EXPORT .GLB**.
6. In Roblox Studio: **File → Import**, choose the `.glb` and import. Resize and anchor the imported MeshPart/Model as needed.

## What it produces

Each surviving image pixel becomes a colored 3D brick with a raised stud. The browser writes glTF 2.0 GLB directly, with vertex colors, normals and material. There are no image-texture dependencies. A model is approximately 3.5 studs along its largest image dimension. Import support: [Roblox Studio Importer](https://create.roblox.com/docs/studio/importer).

**Important limitation:** This is a relief, not an AI-generated full 3D object: the back is flat and there is no inferred anatomy, rounded backside or hidden features. For a fully spherical Tennis Chick, generate a 3D mesh first and then apply a voxel/stud conversion.

## Recommended settings

- Use a cropped subject on a transparent PNG if possible.
- Start with 32–48 studs on the longest edge and 12–20 colors.
- Turn off background removal if it cuts away legitimate parts of the subject.
- Use higher resolution only when the preview and resulting mesh size are acceptable.

## Technical details

- Runs entirely client-side using Canvas 2D for image sampling and WebGL2 for rendering.
- Deterministic, no external libraries or network requests.
- Binary GLB exporter implemented against glTF 2.0 (`POSITION`, `NORMAL`, `COLOR_0`).
- Native triangle mesh, with square or circular studs; one glTF mesh/primitive.
- Default sample is an original generated illustration, not the user's uploaded image.

## License

MIT