# Hack Club Grant Submission Packet: mars0x1_LAB

Use this packet to fill out your Hack Club OnBoard / Highway PCB Grant application. You can copy and paste answers directly into the application form or Slack submission thread.

---

## 1. Quick Info & Links

| Field | Submission Value |
| :--- | :--- |
| **Project Name** | `mars0x1_LAB` |
| **Short Tagline** | ESP32-S3 4-Layer Mixed-Signal Electronics Workstation |
| **GitHub Repository** | [https://github.com/mars0x1/mars0x1_LAB](https://github.com/mars0x1/mars0x1_LAB) |
| **License** | Open Source (MIT License) |
| **EDA Tool** | KiCad 9.0.6 |
| **Gerbers Download** | [`gerbers.zip`](https://github.com/mars0x1/mars0x1_LAB/raw/main/gerbers.zip) |
| **3D Raytraced Preview** | [assets/pcb_3d_render.png](https://github.com/mars0x1/mars0x1_LAB/raw/main/assets/pcb_3d_render.png) |

---

## 2. Project Description / "What is your project?"

> **Copy & Paste for "Describe your project in a few sentences"**:
>
> `mars0x1_LAB` is an all-in-one, 4-layer mixed-signal laboratory workstation designed around the ESP32-S3 microcontroller. It integrates all the essential benchtop instruments an electronics hacker needs into a single unified instrument:
> 1. **4-Channel 10 MHz Analog Oscilloscope** front-end utilizing a precision low-noise OPA4192 rail-to-rail op-amp, REF3025 2.50V reference, and input protection clamping diodes.
> 2. **12.5 MHz Direct Digital Synthesis (DDS) Function Generator** based on the AD9833 with programmable sine/triangle/square waves, digital gain control via MCP4131, and a discrete TIP31C/TIP32C push-pull 50Ω line driver.
> 3. **Dual High-Speed Pulse Generator** with dedicated discrete 2N3904 emitter-follower buffers and digital amplitude adjustment.
> 4. **Benchtop User Interface** featuring 3× ALPS EC11 rotary encoders with tactile pushbuttons for real-time parameter tweaking.
> 5. **Integrated 100% Pure Linear Split Power Supply** (+12V, -12V, +5V) with full-wave rectification and 4000µF reservoir capacitors, completely eliminating high-frequency SMPS switching noise from delicate analog measurements.

---

## 3. Silkscreen Requirement Proof (Hack Club Branding)

> **Copy & Paste for "Does your board feature the Hack Club logo / attribution?"**:
>
> **Yes!** The board prominently displays the Hack Club attribution directly on the top silkscreen layer (`F.SilkS`) in the top-left section:
>
> ```text
> mars0x1_LAB  •  MIXED-SIGNAL WORKSTATION
> 4-CH 10MHz DSO  •  12.5MHz DDS FUNC GEN  •  DUAL FAST PULSE
> ESP32-S3 CORE  •  Designed by mars0x1  •  Powered by Hack Club
> ```
>
> Furthermore, the GitHub repository features the official Hack Club OnBoard badge at the top of the `README.md`.
>
> Proof render: [https://github.com/mars0x1/mars0x1_LAB/blob/main/assets/pcb_3d_render.png](https://github.com/mars0x1/mars0x1_LAB/blob/main/assets/pcb_3d_render.png)

---

## 4. JLCPCB Manufacturing Parameters

When placing your order on [jlcpcb.com/quote](https://jlcpcb.com/quote), upload `gerbers.zip` and select these settings:

| Parameter | Recommended Selection | Notes |
| :--- | :--- | :--- |
| **Dimensions** | `175.59 mm × 134.00 mm` | Auto-detected from Gerber files |
| **Layers** | **4 Layers** | JLC04161H-7628 stackup |
| **Quantity** | 5 pcs | Standard prototype minimum |
| **PCB Thickness** | `1.6 mm` | Standard rigid thickness |
| **Base Material** | FR4 | TG 135–140 |
| **Impedance** | No | Standard clearance is sufficient |
| **Solder Mask** | Green (or Black / Purple) | Your aesthetic preference |
| **Silkscreen** | White | High contrast |
| **Surface Finish** | Lead-free HASL (or ENIG) | Lead-free HASL is most economical; ENIG gives flatter pads for fine-pitch parts |
| **Copper Weight** | 1 oz outer / 0.5 oz inner | Standard 4-layer copper |
| **Via Process** | Tenting / Plugged | Standard tenting |

---

## 5. "What did you learn / What were the hardest engineering challenges?"

> **Copy & Paste for "What did you learn while designing this board?"**:
>
> Designing `mars0x1_LAB` was a huge step forward in mixed-signal hardware engineering:
> 1. **Mixed-Signal 4-Layer EMC & Grounding**: Because sensitive 10 MHz analog signals coexist on the same board as high-speed ESP32-S3 SPI/Wi-Fi digital buses, proper grounding was crucial. I implemented solid internal ground planes stitched together with **220 DGND stitching vias** around high-frequency paths and board edges to minimize return loop inductance and prevent digital switching hash from polluting the scope analog front-end.
> 2. **Analog Front-End Protection & Rail Biasing**: Designing the 4-channel DSO front-end taught me how to protect high-impedance op-amp inputs (`OPA4192`) from over-voltage transients using `BAT54S` Schottky clamping diodes and current-limiting resistors, combined with a `REF3025` 2.5V precision voltage reference for unipolar ADC translation.
> 3. **Thermal Management in Linear Power Supplies**: Rather than using noisy switch-mode buck converters, I opted for a 100% linear power supply (+12V, -12V, +5V). I had to carefully analyze TO-220 tab potentials: `LM7812` tab is tied to ground, but the `LM7912` negative regulator tab is tied to its raw -18V DC rail, and the `TIP31C/TIP32C` output transistors have their collectors tied to ±12V. This taught me the critical importance of heatsink isolation and thermal relief.
> 4. **Precision Mechanical & 3D Alignment in KiCad 9**: I aligned all 7 BNC coaxial connectors, 3 ALPS EC11 rotary encoders, and dual socket layouts for interchangeable AD9833 module pinouts, ensuring zero clearance violations and clean DRC verification.

---

## 6. Submission Checklist

- [x] GitHub repository is public: `https://github.com/mars0x1/mars0x1_LAB`
- [x] Open-source license file (`LICENSE` - MIT) is present in repo root.
- [x] `README.md` includes system specs, front-panel layout, and 3D preview render.
- [x] Production `gerbers.zip` tested, DRC-clean (0 unrouted, 0 clearance errors), and uploaded to repo.
- [x] Hack Club attribution clearly visible on top silkscreen (`Powered by Hack Club`).
- [x] Schematic PDF (`assets/schematic.pdf`) and vector SVGs included for quick reviewer inspection.
