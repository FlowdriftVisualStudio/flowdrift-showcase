# Flowdrift Visual Art Studio 8.18

Open the included `index.html` in Chrome to use this version. The app is self-contained and works offline after downloading. No installation or paid dependency is required. It uses native WebGL, not Three.js.

## Five steps

1. **Photos:** add your pictures or try the new supplied FD sample. Reorder, remove, undo and redo are available.
2. **Art & motion:** choose a starting look or Cycle all looks. Adjust Hue Shift under **Colour & photo surface**. **Shape & nature motion** contains formations, movement and the journey between photo and particles.
3. **Music:** add MP3/WAV, press play, and select **Beat**, **Voice** or **Beat + voice**. Audio sensitivity ranges from 0 to 10. Beat pulse and Voice flow meters show the responses separately.
4. **Size:** choose your social aspect ratio, picture size, and Stationary or Spin. Drag the metal rotation dial up/down, use its keyboard arrows, or use the slider. Speed ranges from 0.1× (15 minutes per turn) to 10× (9 seconds per turn); 1× is 90 seconds.
5. **Export:** save a PNG, record a WebM with playing audio, or save an editable project containing photos, music and settings.

The guide suggests the next step, but all five tabs and Export remain available immediately. Choose **3D orbit** above the preview and drag to orbit; scroll or pinch to zoom. Centre view resets the camera. Focus view hides the controls.

## Version 8.18

Layers composite onto a transparent stack with 23 blend choices. Group editing propagates adjustments to the members. Switch the editing scope to work on one member. Use the four ordering buttons to move individual layers or entire groups. Group spin defaults to rotation around the shared centre in the image plane. Stationary stops spin. The archive includes restore-8.17.html. The 56 logic checks passed. Mac Chrome visual and video fidelity testing is pending.

## Version 8.17

Hue Shift applies to edited photos, particles and the cursor brush. Show Photo bypasses the colour adjustment. The compact selector retains all 16 looks. The controls identify the selected photo and keep Next and Back clear of the scrolling content. Trees, ferns, flowers, butterflies and flocks use new geometry and movement. The archive includes restore-8.16.html. The 54 automated logic checks passed.

## Stage 1 — branding and core editing (8.16)

This extends the existing single-file WebGL application. No renderer replacement or new runtime dependency was introduced.

- The supplied lowercase wordmark appears in the header and welcome area. The supplied FD image is used for the favicon, application icon, loading state and sample. Transparent PNG/WebP derivatives are included under `assets/branding`; the untouched high-resolution uploads are in `assets/originals`. Embedded versions let `index.html` work offline.
- Add up to 24 simultaneous photo layers. Each owns its original media, crop, position, scale, rotation, opacity, blending, effect settings, particle buffers, camera and cursor response. Adding a photo does not change existing photos. Duplicates share immutable original media and retain separate editing settings.
- In **Move / resize** mode, click a photo to select it, drag to move, drag its lower-right handle to resize, and use its top handle to rotate. **Size** retains the picture-size slider and rotation-speed dial. Choose **3D orbit** to orbit the selected photo. The Photos panel also has numerical-position sliders, crop margins and opacity.
- Layer rows offer selection, visibility and locking. Send backward / Bring forward changes stacking order (and slideshow order). Tick layers to group them; canvas handles transform the unlocked members together. Sliders affect only the selected photo. Ungroup restores individual canvas movement. Arrange all lays visible, unlocked photos out in a grid.
- **Show photo** instantly displays the selected original, bypassing its crop, materials, particles, rotation and distortion, while preserving its placement and scale for comparison. **Back to edits** restores the edited view. This works while paused or playing. **Reform** retains the previous animated reconstruction.
- Undo and Redo now sit immediately beside Pause, with Command+Z / Command+Shift+Z (Control equivalents on other systems). **Undo this photo / Redo this photo** operate independently. The adjustable 32/64/128/256 MB history budget evicts oldest undo states; original media remains intact. History belongs to the current session, not the project file.
- A persistent **File ready** card provides a direct download link if Chrome does not start an automatic download. Header Save/Open use editable `.flowdrift` projects. Version 2 stores all layers, asset references, groups, locks, visibility, materials, crop, cameras, comparison flags and global audio/framing settings. Existing version 1 projects migrate to the preserved single-photo slideshow mode. Invalid imports leave the current scene intact.
- The original slideshow is still available: choose **One photo / slideshow**, or Play slideshow. **All photo layers together** restores the composition view. PNG and real-time WebM capture the composite artwork canvas.

**Next stages are not implemented yet:** the full animation timeline, per-control keyframes and easing editor (Stage 2); expanded effects (Stage 3); detailed people/animals/zodiac and mathematical systems (Stage 4); new audio controls, deterministic video rendering and MP4/MOV conversion (Stage 5); full final stability and performance testing (Stage 6). Existing timing strips are not a keyframe editor. Current export formats remain PNG and WebM.

**Restore point:** `restore/studio-8.15-before-layers` in the development repository; the download also contains `restore-8.15.html`. Open that file to use the preceding working version. Keep your original `.flowdrift` files when migrating; version 2 files need 8.16 or later.

## What changed in 8.15

- The photo is now a 72×72 deformable mesh. Liquid push, Bubble lens, Gentle ripple, Whirlpool twist, Pinch & pull, Elastic stretch, Melting waves and Crystal facets deform actual geometry beyond the original photo outline. The selected export frame remains the outer crop.
- A shared cursor field applies those same modes to every particle material, in the same screen coordinates and with the same brush size. Exponential pointer smoothing has no spring or rebound. Particle brush trails gather home over 1.8 seconds with a monotonic fade; their return directions no longer oscillate.
- The particle brush now uses the selected particle material, including the new natural shapes. Photo colours remain enabled by default. Disable that option for stylised palettes.
- Nine new materials bring the total to **28**: windblown leaves, translucent petals, feather wisps, golden pollen, glass raindrops, branching snowflakes, weathered bark, fluttering butterflies and little people.
- Seven new formations bring the total to **19**: human figure, dancing figure, branching tree, fern, wildflower, butterfly and a flock of birds. Six new ready-made looks join the ten previous looks.
- Six nature movement choices: breeze, ocean currents, butterfly flutter, floating seeds, opening bloom and birdlike swarms. Four curved transition journeys: wind lift, seed spiral, ocean curl and petal unfurl. The original direct flow remains available. Curved paths have zero offset and zero slope at their endpoints, and reform to the original photo coordinates.
- Voice response uses a smoothed 300–3400 Hz spectral envelope; it follows speech/singing and instruments in the same range. It is not voice isolation, source separation or speech recognition. Beat mode detects rises in low-frequency energy, not a BPM grid. Both combines the two responses with bounded intensity.
- All new choices save in projects and support undo/redo. Older projects receive compatible defaults: original flow, beat response and 1× rotation speed. Looks retain audio, framing and rotation choices.

## Existing features retained

Photo sequencing with adjustable holds, scatter/reform, thirteen previous particle materials plus the five 8.14 materials, eleven photo surfaces, image scaling, landscape/portrait/square exports, audio upload, project reopen, pause, slideshow, look cycling, PNG and WebM export remain available. Chrome UI reflections and buttons do not appear in exported artwork. Reduced-motion preferences stop decorative interface animation.

Pause freezes artwork, cursor response, sequence and audio. A recording continues capturing the frozen picture until stopped. Manual formation/photo actions stop the slideshow and look cycle. Cursor positions and transient playback are not saved in projects.

## Limits

- Materials, nature motion and voice response are procedural visual approximations, not physical cloth/fluid simulation or vocal isolation.
- On touchscreens, one-finger dragging applies the selected cursor effect while React to cursor is enabled; lifting eases the image and particles back. Two fingers retain pinch zoom. Turn React to cursor off to move a photo, or choose 3D orbit for one-finger camera movement. Mouse hover and mouse editing are unchanged.
- WebM recording is real time, up to 3 minutes or 200 MB; it does not create MP4. Playing audio is included. Tracks do not automatically loop.
- Imports allow 30 MB per photo, 60 MB audio, 180 MB embedded media total, and 250 MB project files. GPU photo textures are limited to 4096 pixels or the device maximum; original project media is retained.
- Files stay in the browser unless you save a project or export. No analytics, external scripts or runtime network dependencies are used.

## Validation

`node --test tests/logic.test.cjs` executes the real inline app with simulated DOM/WebGL/audio boundaries. The 51 regression tests cover layer isolation, non-destructive crops, duplication, grouping, locking, per-photo history, original comparison, v1/v2 project compatibility and all previous checks: navigation, media editing, undo/redo, project compatibility, recording controls, pause, timing, exact photo reconstruction, new formation bounds, continuous interrupted transitions, smooth cursor settling, vocal/bass separation and rotation speed ratios.

All three shader programs also compile and link on Mesa EGL/OpenGL ES. Native GPU pixel checks verify all eight mesh distortion modes change the actual photo silhouette, extend beyond the original outline, and restore identical pixels at zero response. These checks do not establish device-specific frame rates, music quality or encoding compatibility.

`tests/studio.spec.cjs` is an optional Playwright test for a local development environment with Chromium. It covers exports, photo editing and responsive screenshots. Local Chromium cannot run in the current restricted host. Live Chrome checks are performed against the deployed page separately.

