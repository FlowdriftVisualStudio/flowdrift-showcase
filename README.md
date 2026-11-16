# Flowdrift Visual Art Studio

Open `index.html` in Chrome (double-click the downloaded file). No installation, server, account, or external scripts are needed. The original `visual_art_studio_8_1.html` is preserved.

## Workflow

Studio 8.9 uses one task panel: **Photos → Looks → Music → Size → Export**. The active tab is highlighted; the artwork stays visible in a larger preview. Chrome reflections and the metallic wordmark respect reduced-motion preferences.

1. **Photos:** add photographs, select a thumbnail, or remove a photo. Reordering is under More photo options.
2. **Looks:** preview ten looks: Silk Bloom, Dreamflow, Vortex Storm, Orbit Lights, Galaxy Burst, Aurora Veil, Cosmic Dust, Smoke Bloom, Concrete Break and Liquid Metal. Choose a particle material, then adjust speed and glow. Timing and detailed adjustments are expandable.
3. **Music:** upload a track, press play, and adjust beat sensitivity from 0 to 10. A live beat meter shows detected pulses. Music affects pulsing, movement, glow and material intensity.
4. **Size:** select 9:16, 4:5, 1:1 or 16:9, then adjust Picture size or Fit whole photo. Choose Stationary or Slow spin; a full turn takes about 90 seconds. This choice survives changes of look and pauses with the studio. Outside black bars are excluded from exports.
5. **Export:** save PNG, record WebM, or save/reopen an editable project containing media, settings and camera. Refreshing alone does not save your work.

The bottom buttons are **Play slideshow**, **Animate once**, **Show photo**, and **Pause / Resume**. “Centre view” resets the camera. You can try the supplied sample before uploading photos.

## Notes

- Pause freezes the artwork, sequence, ripple and audio. Recording continues capturing that frozen picture until stopped.
- Manual photo/formation actions stop the automatic sequence to prevent competing actions.
- Undo/redo covers photo edits, settings, presets, and audio selection. It does not rewind animation or recordings.
- Liquid materials are stylised GPU effects on the photograph's plane, following its camera; they are not fluid simulation or materials on individual particles.
- Recorded audio is included when a loaded track plays. Play audio before recording or enable “Start audio with sequence” and start the sequence. Audio does not automatically loop.
- Recording is real-time, limited to 3 minutes or approximately 200 MB of accumulated chunks. Save longer pieces in sections. Browser support and available memory vary; WebM is not MP4.
- Files remain in the browser unless you explicitly save/download a project or export. Project files embed media and may be large. There are no analytics or network dependencies.
- Import limits: 30 MB per image, 60 MB for audio, and 180 MB total embedded media. Project files: 250 MB maximum. These are safeguards, not a guarantee that every device can handle the maximum.
- The photo plane is fitted using the original aspect ratio. Very large source photos are reduced only for the GPU texture; project files retain the originals.
- On phones, the task panel sits below the preview. Drag to orbit and use two fingers to zoom. Use Chrome on desktop for the most predictable recording support.

## Validation

Run `node --test tests/logic.test.cjs` for dependency-free logic regressions. These execute the actual inline application code with simulated DOM, graphics and audio boundaries: they verify state and timing, not rendered pixels or codecs.

`tests/studio.spec.cjs` provides a separate real-browser smoke test. With Playwright and Chromium installed, run `node tests/studio.spec.cjs`; optionally set `CHROMIUM_PATH` to your Chromium executable. It checks WebGL startup, frozen frames, photo editing, project reopening, PNG dimensions, a short WebM recording, and responsive screenshots. Its outputs are written into a temporary directory printed at completion.

At implementation time, JavaScript syntax, particle, photo and brush shader compilation/linking on Mesa EGL, and 29 logic regression tests passed, including the five-tab workflow, morph handover, social framing and audio band analysis. Real-browser testing could not run: local Chromium was denied a required process socket, and the connected browser rejected the local preview URL protocol. Visual rendering, audio quality/synchronisation, actual encoding, and device performance still require manual validation. The browser smoke test is included but has not passed in this environment.

## Interface references

The navigation borrows general interaction patterns, not code or assets: Resolume’s at-a-glance dashboard (https://resolume.com/index.php/support/en/dashboard), Synesthesia’s purpose-based control groups (https://app.synesthesia.live/docs/manual/controls.html), and Canva’s persistent video timeline (https://www.canva.com/help/creating-and-editing-videos/).

## Expanded effects

Eight procedural particle materials: glow dots, silk fibres, silk dust, soft smoke, concrete grain, chrome beads, starlight and ember sparks. These are stylised shader textures, not physically simulated smoke, cloth or concrete. Particle materials are independent of intact photo surfaces. Texture detail and shape movement live under Advanced adjustments → Particles & shapes.

Ribbon, nebula and light-fountain formations join the existing shapes. Galaxy and vortex rotate differentially; ribbons undulate and clouds swell. Silky drift, Dream flow, Galaxy sweep, Aurora waves and Light fountain motion presets preview immediately while retaining the current particle material. All shapes can reform into the photo. Choosing a full look preserves your photo selection, music response and export framing.

Stationary means no automatic camera rotation; music pulses and particle animation remain independent. Beat response uses frequency-energy rises rather than a fixed tempo grid; it is not BPM detection. Old saved projects default to Stationary. The chrome background and coloured glass controls are interface styling and do not appear in exported artwork. Reduced-motion preferences stop decorative interface animation.

Studio 8.9 adds a self-contained SVG glass ribbon emblem: a continuous flowing wave with a second drifting trail, shaded orange, purple and blue. Five raised metallic tabs have individual warm orange, purple, blue, teal and rose finishes. In Looks, Cycle all looks visits all ten styles, allowing each transition to finish and holding it for four seconds before the next. Pause freezes the cycle; Stop cycling retains the current style. Picking a style or using a manual photo/formation action stops cycling. The cycle is transient playback state, not saved autoplay.

## Guided setup

A five-step guide starts on Photos. Follow Next through Looks, optional Music, Size and Export, or open any tab directly. Back revisits the previous step. All tabs and the header Export button remain accessible from startup; no photo upload or look selection is required to unlock navigation. Studio 8.9 fixes the navigation locks introduced in 8.7 while retaining the instructions and progress indicator.

## Studio 8.9 materials and finish

Six new animated particle materials bring the total to fourteen: Opal gel droplets (moving pearlescent highlights), Prismatic shards (rotating rainbow facets), Iridescent bubbles (breathing spectral rims), Plasma filaments (travelling electric waves), Liquid foil flakes (folded reflective flashes), and Cosmic ripple rings (expanding concentric light). Choose Looks → Particle material. Existing size, texture detail, music response, pause and photo reconstruction apply to these materials. They are procedural visual effects, not physical refraction simulations.

Buttons use translucent tinted metal, reflected highlights and embossed edges. The Flowdrift wordmark uses a clean bold sans-serif font, bright glass highlights and dark dimensional shadows for contrast. Fonts come from the device, so it works offline.

Studio 8.9.1 corrects the wordmark to Flowdrift as one word and simplifies its lettering for readability.

## Studio 8.10 photo surfaces

Looks → Photo surface now includes Sculpted glass (rolling polished ridges), Holographic foil (moving rainbow folds), Living opal (drifting pearlescent patches), Aurora silk (luminous satin waves), Luminous mineral veins (pulsing coloured seams), and Prismatic waves (radial caustics and colour separation). These six additions preserve the original photo beneath their animated effects. They are stylised shader effects rather than physical material simulations.

Colour & surfaces controls intensity, viscosity (animation pace), ripple scale (pattern size) and reflectivity. Zero intensity returns the six new surfaces to the original photo, apart from any separately triggered ripple. Pause freezes them. Music modulates their intensity through the existing beat response. They are saved in projects and rendered in photo/video exports. Select Original photo to remove the surface.

## Studio 8.11 cursor response

Looks → React to cursor is on by default. Moving the mouse over the artwork gently shifts the view, makes local photo ripples, and pushes scattered particles around the pointer. Cursor response adjusts strength from 0 to 2. Movement eases back after leaving the artwork; Pause freezes it. Disable React to cursor for a fixed view. Drag-to-orbit, scroll-to-zoom and touch orbit/pinch remain available. Touch has no hover effect. Cursor settings save with projects; transient pointer positions do not. Live cursor effects appear in exports while active.

## Studio 8.12 liquid cursor distortion

Under Looks, Cursor distortion offers Liquid push (pulls and swirls the photo pixels with mouse movement), Bubble lens (local bulging magnification), Gentle ripple, or Movement only. Liquid push is the default. Bubble / liquid size changes the affected area; Cursor response controls strength. The photo deforms locally, including when Original photo is selected. Edges are softened and sampling is clamped. Pointer velocity eases back to zero when you stop, and the effect fades away when you leave the artwork. These effects are non-destructive and use the original image texture.

## Studio 8.13 particle brush

The default cursor effect is now Particle brush, based on the supplied video. Sweeps lift fine grains coloured from the photo, revealing a local opening. The grains drift out and gather back as a short trail fades over 1.8 seconds. Brush size and Cursor response adjust the area and strength. The photo stays steady in this mode. Liquid push, Bubble lens and Gentle ripple remain selectable. Pause freezes the trail; disabling cursor response clears it when playback resumes.
