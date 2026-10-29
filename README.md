## Sampling Space: DIY Spatial Room Impulse Response Capture for Creative Applications
### *AES Show Nashville, 2026*


The following notebook accompanies the above workshop on conducting Spatial Room Impulse Response (SRIR) measurements for creative applications. It includes simulated data for the SRIR recording and processing pipeline. Real world measurement scenarios require the appropriate loudspeaker output, microphone array (spaced array, binaural, ambisonic), and careful equipment calibration.

### Contents

0. Setup
1. Sweep Generation
2. Deconvolution

Optional Sections

3. Other Types of Test Signal
4. Frequency Domain Deconvolution Method
5. Instantaneous Frequency and Spectral Representation
6. Harmonic Distortion Separation
7. From Mono RIR to Simulated B-Format SRIR

### Quick-start workflow

- **Run the notebook once from top to bottom** (`Runtime → Run all` in Colab). This creates the folders, generates a sweep, simulates a room recording, and demonstrates deconvolution.
- **Generate and download the sweep.** In Section 1, adjust the parameters in Participant Cell 1 if needed, then run Participant Cells 2–3. The 24-bit WAV is saved in **`ESS`**.
- **Measure the room.** Play that WAV in Reaper through your loudspeaker and record the room response. Export the recording as a WAV at the **same sample rate** as the sweep.
- **Upload the recording.** Put the exported WAV in **`ESSresponses`** (in Colab, use the Files panel; storage is temporary, so download any files you need to keep).
- **Recover the impulse response.** In Section 2, make sure Participant Cell 4 uses the same sweep settings, then set `my_recording_file` in Participant Cell 7 to your WAV's filename and run that cell. The recovered response is saved as a 32-bit float WAV in **`Deconvolved output`**. Set `download_to_computer = True` in Participant Cell 3 if you also want the generated sweep downloaded automatically; the same option enables downloads of deconvolved outputs in Colab.

### Folders

- **`ESS`** — generated sweep WAV files for playback in Reaper.
- **`ESSresponses`** — recordings made in the room; upload or copy your recording here.
- **`Deconvolved output`** — recovered impulse responses.

The folders are created by the setup cell in the notebook's current working directory. In Colab, view them in the **Files** panel on the left; refresh the panel if a new file does not appear. Right-click a file to download it.

### Participant cells and optional material

- The numbered **Participant Cells** are the main cells to edit or run during the workshop. Run them in order when first starting; after changing sweep parameters, rerun Participant Cells 1–4 to regenerate the sweep and matching inverse filter. If you are using a newly recorded real response, rerun Participant Cell 7 after updating `my_recording_file`.
- Sections 4–7 are optional extensions. They demonstrate alternative deconvolution and additional signal/spatial-acoustics concepts; they are not required for the core workflow.
- Collapse or expand sections with the chevron beside each section heading.
