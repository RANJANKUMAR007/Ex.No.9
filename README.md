# Ex.No.9: Exploration of Prompting Techniques for Video Generation

**Date:** 02-09-2026  
**Register No:** 212223040138  

---

## 1. Aim
To investigate, implement, and evaluate multi-tier prompting techniques for AI text-to-video synthesis, demonstrating how progressive prompt structuring—controlling spatial parameters, temporal vectors, camera kinematics, and physical dynamics—enables the systematic reproduction of target reference video sequences while maintaining frame-to-frame coherence.

---

## 2. Technical Framework: Generative Video Architectures

Text-to-video (T2V) systems extend 2D spatial diffusion architectures into 3D spatiotemporal representations by introducing temporal attention layers or spatiotemporal patch transformers:

$$\mathcal{V}_{\text{clip}} = \mathcal{G}_{\theta}\Big(z_t, \; \tau_{\theta}(P_{\text{spatial}}), \; \tau_{\theta}(P_{\text{temporal}}), \; \mathcal{C}_{\text{camera}}\Big)$$

Where:
* $z_t$ represents the latent noisy video tensor across dimensions $(B, C, F, H, W)$.
* $\tau_{\theta}(P_{\text{spatial}})$ encodes static scene attributes (geometry, identity, illumination).
* $\tau_{\theta}(P_{\text{temporal}})$ encodes kinetic flow vectors (velocity, fluid mechanics, rigid motion).
* $\mathcal{C}_{\text{camera}}$ specifies perspective trajectory (dolly, pan, tilt, orbit, tracking speed).

### Benchmark Comparison of Generative Video Platforms

| Tool / Platform | Underlying Architecture | Primary Input Modality | Native Resolution & FPS | Motion Control Levers |
| :--- | :--- | :--- | :---: | :--- |
| **Runway Gen-3 Alpha** | Diffusion Transformer (DiT) | Text / Image / Video | 1080p @ 24/30 FPS | Motion Brush, Multi-camera paths, Speed curves |
| **OpenAI Sora** | Spatiotemporal DiT Patches | Text / Image | Up to 1080p @ 60 FPS | Natural language camera directives, Physics continuity |
| **Pika 2.0** | Latent Diffusion Model (LDM) | Text / Image | 720p/1080p @ 24 FPS | Pan/Tilt sliders, Zoom factor, Region modify |
| **Stable Video Diffusion (SVD)** | 3D Latent UNet | Image-to-Video | 576×1024 @ 14/25 FPS | Motion Bucket ID (1–255), Augmentation Level |

---

## 3. End-to-End Experimental Architecture

```text
               [Target Reference Video Stream]
                              │
                              ▼
        [Spatiotemporal Feature Extraction & Auditing]
        ┌─────────────────────┴─────────────────────┐
        ▼                                           ▼
 [Spatial Domain Attributes]               [Temporal Dynamics Vector]
 • Static Geometry & Objects               • Subject Kinematics & Velocity
 • Material Roughness & Albedo             • Camera Motion & Lens Metrics
 • Environmental Key/Fill Ratio            • Fluid / Particle Physics Engine
        └─────────────────────┬─────────────────────┘
                              │
                              ▼
           [Multi-Tier Structured Prompt Pipeline]
  Level 1 (Naive) ──► Level 2 (Parametric) ──► Level 3 (Production)
                              │
                              ▼
              [T2V Latent Diffusion Inference]
                              │
                              ▼
      [Comparative Frame Audits & Temporal Metrics Review]
