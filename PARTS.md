# How to swap the car

The website shows whatever is in **`car.glb`**. To update the car, replace that one file and redeploy. Nothing else changes.

## The short version
1. Export your car as **glTF Binary (.glb)**.
2. Name the **materials** using the list below. The site uses material names to work out what each part is.
3. Save it as `car.glb` and replace the old file.
4. Redeploy (or push to GitHub if Vercel is connected to it).

## Material names → what the site does with them

| Material name | Used for | What the site does |
|---|---|---|
| `paint` | Body panels, mirrors | Applies the colour sliders, sparkle flake and clear coat |
| `glass` | Windows | Dark tinted glass with reflections |
| `trim` | Window frames, pillars, sills | Gloss black |
| `louvre` | Engine-cover slats | Black with a slatted surface |
| `carbon` | Splitter, diffuser, fins | Woven carbon fibre |
| `opening` | Grille holes, intakes, scoop mouth | Near-black |
| `black` | Arch liners, small black bits | Matte black |
| `underbody` | Floor pan, engine block | Dark grey |
| `tyre` (or `tire`) | Tyres | Rubber |
| `rim` | Wheel spokes | Polished alloy |
| `rim_dark` | Rim barrel, badges, arms | Dark metal |
| `brake_disc` | Brake discs, exhaust pipes | Steel |
| `caliper` | Brake callipers | Red gloss |
| `exhaust_tip` | Exhaust tips | Heat-tinted titanium |
| **`head_light`** | Front light tubes / LED strips | **Glows white with the Headlights switch** |
| **`head_lens`** | Glass inside the headlights | Soft white glow |
| **`tail_light`** | Rear light tubes / segments | **Glows red with the Taillights and Brake switches** |
| **`tail_lens`** | Glass inside the taillights | Soft red glow |

- Names don't need to be exact: `Paint.001`, `car_paint` and `PAINT` all count as `paint`.
- A material with a name that isn't on the list keeps its own look. The browser console lists any unrecognised names.

## Optional extras (nice to have)
| Node name | What it does |
|---|---|
| `wire_<part>` | Line-only copy of a part. Used in **Wireframe** mode, so you see clean four-sided panel lines instead of triangles. Without it, the site draws the part's edges automatically. |
| `marker_head_L` / `marker_head_R` | Empty object where each headlight beam starts |
| `marker_head_L_aim` / `marker_head_R_aim` | Empty object each beam points at |
| `marker_tail_L` / `marker_tail_R` | Empty object for the red glow on the floor behind the car |
| `wheel_FL_…`, `wheel_FR_…`, `wheel_RL_…`, `wheel_RR_…` | Wheel parts. Not required yet; reserved for spinning wheels later |

Without markers, the site places the lights from the `head_light` and `tail_light` parts.

## Size and direction
- **Best:** metres, nose pointing **+Z**, Y up, wheels touching Y = 0.
- **The site fixes these automatically:**
  - Wrong units (for example centimetres): scaled to a 4.6 m long car.
  - Car lying sideways: turned 90°.
  - Car facing backwards: turned around, using where the headlights and taillights are.
  - Off-centre: centred, with the wheels put on the floor.

## Tips
- Keep the file under ~5 MB, because phones download it.
- Paint sparkle looks right when the paint's UVs are roughly in metres. If the flakes look too big or too small, use the **Flake size** slider.
- Light tubes look best as real tube geometry, about 1–2 cm thick, sitting on the surface.

## Exporting from Blender
File → Export → glTF 2.0 → Format: **glTF Binary (.glb)**. Under Include, tick **Custom Properties**. Under Transform, keep **+Y Up**. Materials can be simple; the site replaces them by name.
