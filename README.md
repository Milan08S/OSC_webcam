# Interactive Systems - Workshop 2

## Team Members
- Miguel Angel Sanchez Paez  
- Julio Alejandro Mazo Reyes  

---

## Description

- This project creates a **real-time interactive system** that connects camera input with sound generation using **Pure Data**. The system analyzes visual properties like RGB color values, brightness, and contrast from the camera feed, and translates them into dynamic audio output.

- When the camera captures visual changes, the sound immediately responds, creating an interactive audiovisual experience.

---

## How It Works

The Pure Data patch receives data through OSC protocol on port 5005. This data contains:
- **RGB values** from the camera image
- **Brightness levels**
- **Contrast information**

These values are processed and routed to different sound generation modules that produce musical notes using the `makenote` object.

---

## Design Justification

### Color-to-Sound Mapping
- Each RGB channel is mapped to pitch values. The RGB values (0-255) are scaled and combined to create frequencies that vary based on the colors detected by the camera. This creates an intuitive relationship where different colors produce different tones.

### Brightness Compensation
A key design decision was **adding 500 to the brightness value when it is below 300**. 

**Why?**
- Without this adjustment, low brightness values (0-300) would produce extremely low frequencies that are difficult to hear or fall outside the audible musical range
- By adding 500 when brightness < 300, we shift these values to an audible range (500-800)
- This ensures that even in dim lighting conditions, the system continues producing clear, perceptible sounds
- The threshold of 300 was chosen to maintain smooth transitions while keeping all notes audible

### Contrast Modulation
Contrast values are used to modulate note characteristics, adding another layer of sonic expression based on visual sharpness.

---

## Pure Data Patch

![Pure Data Patch](./T2.JPEG)

---

## Features

- Real-time color detection and sound mapping.
- Brightness-based frequency adjustment.
- Low-light compensation for consistent audibility.
- Contrast-based sound modulation.
- Immediate audio response to visual changes.