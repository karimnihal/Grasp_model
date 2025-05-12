# Cornell‑Style Grasping Dataset Card (Extended)

## 1. Directory Layout

```

data/
├── 01/ … 10/          # Ten object folders with RGB‑D scenes + grasp labels
│   ├── pcdXXXX.txt    # (optional) legacy metadata for grasp rectangles
│   ├── pcdXXXXcpos.txt# positive grasp rectangles (good grasps)
│   ├── pcdXXXXcneg.txt# negative grasp rectangles (failed grasps)
│   ├── pcdXXXXr.png   # aligned RGB image
│   └── pcdXXXXd.tiff  # aligned 16‑bit depth map
└── backgrounds/       # Background‑only RGB images for augmentation
├── pcdb0001r.png
└── …

```

> **Naming convention**   
> `XXXX` is a four‑digit index—e.g. `0100`, `1034`, etc.  
> Each index corresponds to one *data point* with up to five companion files.

---

## 2. Files Per Data Point

| File | Modality | Purpose / Contents |
|------|----------|--------------------|
| `pcdXXXX.txt` | **Metadata** (text) | Legacy grasp metadata (center x y, angle rad, gripper width). Often unused but kept for backward‑compatibility. |
| `pcdXXXXcpos.txt` | **Labels** (text) | *Positive* grasp rectangles—ground‑truth grasps that succeeded in physical trials. |
| `pcdXXXXcneg.txt` | **Labels** (text) | *Negative* grasp rectangles—known failure grasps. |
| `pcdXXXXr.png` | **RGB** (PNG) | 640 × 480 (default) color image of the scene. |
| `pcdXXXXd.tiff` | **Depth** (TIFF‑16) | 640 × 480 depth map registered to the RGB frame; depth in millimetres. |

### Grasp‑Rectangle Format (`cpos` / `cneg`)

Each line encodes one oriented rectangle:

```

x\_center  y\_center  θ  opening\_width  height

```

- `x_center, y_center` – pixel coordinates of rectangle centre  
- `θ` – rotation (radians, CCW from image x‑axis)  
- `opening_width` – projected gripper width (pixels)  
- `height` – rectangle thickness (pixels)

---

## 3. `backgrounds/` Folder

Standalone RGB images without objects (`pcdbXXXXr.png`).  
Typical uses:

- Domain randomisation or compositing for synthetic augmentation  
- Background subtraction in pre‑processing  
- Generalisation testing on unseen scenes  

No depth or label files are provided for these images.

---

## 4. Dataset Summary

- **Total folders:** 10 object folders + 1 background folder  
- **Per‑object folder:** dozens of RGB‑D frames with paired positive & negative grasp sets  
- **Annotations:** oriented rectangles following the original Cornell Grasp Dataset format  
- **Intended tasks:** grasp detection, grasp quality classification, RGB‑D representation learning, augmentation with background scenes

For citation of the original grasp format, see: Lenz et al., *Deep Learning for Detecting Robotic Grasps*, IJRR 2015.

